# 天眼查 MCP 调用清单

> 队伍：小盾未来队 | 题目：基础题

## 调用统计汇总

| 序号 | 工具类别 | 工具名称 | 调用方式 | 用途说明 |
| --- | --- | --- | --- | --- |
| 1 | 企业类 | `search_companies` | 工作流 MCP 节点 | 企业主体搜索和候选主体确认 |
| 2 | 企业类 | `get_company_basic_profile` | 工作流 MCP 节点 | 企业基本工商信息与基础画像获取 |
| 3 | 企业与关联类 | `get_group_info` | 工作流 MCP 节点 | 集团归属、控制关系和关联结构穿透 |
| 4 | 企业与关联类 | `get_equity_ratio` | 工作流 MCP 节点 | 股权控制结构及疑似实际控制人路径查询 |
| 4 | 董监高类 | `get_company_people` | 工作流 MCP 节点 | 法定代表人、董事、监事和高管信息获取 |
| 5 | 董监高类 | `get_person_risk_profile` | 工作流 MCP 节点、人员风险循环 | 法定代表人和主要人员风险画像查询 |
| 6 | 经营类 | `search_bids` | 工作流 MCP 节点 | 招投标、资产处置等经营线索查询 |
| 7 | 知识产权类 | `search_patents` | 工作流 MCP 节点 | 专利及技术活动线索查询 |
| 8 | 风险类 | `get_risk_overview` | `call_tool` 循环调用 | 企业自身、周边和预警风险总览 |
| 9 | 风险类 | `get_judicial_case` | `call_tool` 循环调用 | 司法案件查询 |
| 10 | 风险类 | `get_judgment_debtor_info` | `call_tool` 循环调用 | 被执行人信息查询 |
| 11 | 风险类 | `get_dishonest_info` | `call_tool` 循环调用 | 失信被执行人信息查询 |
| 12 | 风险类 | `get_high_consumption_restriction` | `call_tool` 循环调用 | 限制高消费信息查询 |
| 13 | 风险类 | `get_administrative_penalty` | `call_tool` 循环调用 | 行政处罚信息查询 |
| 14 | 风险类 | `get_serious_violation` | `call_tool` 循环调用 | 严重违法失信信息查询 |
| 15 | 风险类 | `get_equity_freeze` | `call_tool` 循环调用 | 股权冻结信息查询 |

风险专项调用流程为：先通过 `get_company_capabilities` 获取目标企业可调用工具及参数要求；再由“提取工具”节点生成 `tool_name`、`company_name` 和 `arguments`；最后在“循环获取企业风险”中逐项调用 `call_tool`，并将结果汇入风险评分节点。

## 覆盖统计

| 类别 | 覆盖工具数 |
| --- | ---: |
| 企业类 | 2 |
| 企业与关联类 | 2 |
| 董监高类 | 2 |
| 经营类 | 1 |
| 知识产权类 | 1 |
| 风险类 | 8 |
| **合计** | **6 类别 / 16 个不同工具** |

> 满足赛题要求：通过 AgentArts 接入天眼查 MCP，实际调用不少于 2 个类别、3 个不同工具；本工作流覆盖企业、企业与关联、董监高、经营、知识产权和风险等 6 个类别、16 个不同工具。
