# **structured-response**
A lightweight Python package to generate structured HTTP responses with optional trace IDs. Simplifies API response consistency in Flask-based microservices.

## **Installation**
To install the package, run:
```sh
pip install structured-response
```

Alternatively, install directly from the source:
```sh
pip install git+https://github.com/rohaan2614/structured-response.git
```

## **Usage**
### **Example 1: Basic Response**
```python
from structured_response import generate_response

response = generate_response(
    status_code=200,
    message="Hello, world!"
)
print(response.get_json())  # {"status": "Success", "message": "Hello, world!"}
```

### **Example 2: Custom Trace ID**
```python
from structured_response import generate_response

response = generate_response(
    status_code=404,
    trace_id="abc123",
    message="Resource not found",
    user="John Doe"
)
print(response.get_json())
# Output:
# {
#     "status": "Client Error",
#     "message": "Resource not found",
#     "user": "John Doe"
# }
```

## **Function Reference**
### **`generate_response(status_code: int = 200, trace_id: str None, message: str = None, **kwargs) -> Response`**
Generates a structured HTTP response.

| Parameter | Type | Description |
|-----------|------|-------------|
| `status_code` | `int` | HTTP status code (default: `200`) |
| `trace_id` | `str` | `None` | Unique identifier for tracing requests (optional) |
| `message` | `str` | `None` | Custom message to include in the response (optional) |
| `**kwargs` | `dict` | Additional key-value pairs to include in the response body |

---

## **Development**
Clone the repository:
```sh
git clone https://github.com/rohaan2614/structured-response.git
cd structured-response
```

Install dependencies:
```sh
pip install -r requirements.txt
```

---

## **Changelog**
### **v0.1.1**
- Updated package to use `pyproject.toml` for PEP 625 compliance.
- No functional changes to the code.

### **v0.1.0**
- Initial release 🎉
- Added `generate_response` function with optional `trace_id` support.
- Categorizes status codes (`Informational`, `Success`, etc.).

