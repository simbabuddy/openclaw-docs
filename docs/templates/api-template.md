# API 文档模板

---

# [API 名称]

_简短描述_

**版本：** v1.0  
**状态：** 稳定/测试中/已废弃  
**最后更新：** YYYY-MM-DD

---

## 概述

[API 的用途和功能简介]

---

## 认证

### 认证方式
- Bearer Token
- API Key
- OAuth 2.0

### 获取 Token
```bash
curl -X POST https://api.example.com/auth/token \
  -H "Content-Type: application/json" \
  -d '{"username": "user", "password": "pass"}'
```

### 使用 Token
```bash
curl -X GET https://api.example.com/endpoint \
  -H "Authorization: Bearer YOUR_TOKEN"
```

---

## 端点

### [HTTP 方法] [路径]

_功能描述_

#### 请求头

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| Authorization | string | 是 | Bearer Token |
| Content-Type | string | 是 | application/json |

#### 请求参数

| 字段 | 类型 | 必填 | 说明 | 示例 |
|------|------|------|------|------|
| param1 | string | 是 | 参数说明 | "value" |
| param2 | number | 否 | 参数说明 | 123 |

#### 请求示例

```bash
curl -X GET https://api.example.com/endpoint?param1=value \
  -H "Authorization: Bearer YOUR_TOKEN"
```

#### 响应示例

**成功响应 (200)**
```json
{
  "status": "success",
  "data": {
    "id": 1,
    "name": "example"
  }
}
```

**错误响应 (400)**
```json
{
  "status": "error",
  "code": "INVALID_PARAM",
  "message": "参数错误"
}
```

#### 错误码

| 状态码 | 错误码 | 说明 |
|--------|--------|------|
| 400 | INVALID_PARAM | 请求参数错误 |
| 401 | UNAUTHORIZED | 未授权 |
| 403 | FORBIDDEN | 禁止访问 |
| 404 | NOT_FOUND | 资源不存在 |
| 500 | INTERNAL_ERROR | 服务器内部错误 |

---

## 使用示例

### Python
```python
import requests

response = requests.get(
    'https://api.example.com/endpoint',
    headers={'Authorization': 'Bearer YOUR_TOKEN'},
    params={'param1': 'value'}
)
print(response.json())
```

### JavaScript
```javascript
fetch('https://api.example.com/endpoint?param1=value', {
  headers: {
    'Authorization': 'Bearer YOUR_TOKEN'
  }
})
.then(res => res.json())
.then(data => console.log(data));
```

---

## 限流

| 级别 | 限制 |
|------|------|
| 普通用户 | 100 次/分钟 |
| VIP 用户 | 1000 次/分钟 |

---

## 变更日志

| 版本 | 日期 | 变更内容 |
|------|------|----------|
| v1.0 | YYYY-MM-DD | 初始版本 |

---

## 相关文档

- [相关 API 1](link)
- [相关 API 2](link)

---

_文档版本：v1.0 | 维护：开发团队_
