# Postman API Testing Portfolio

This folder contains Postman collections and test results demonstrating API testing skills across **unit testing** and **integration/flow testing** for a RESTful `/objects` API.

---

## Folder Contents

| File | Description |
|------|-------------|
| `unit-test-collection.json` | Postman collection with unit tests for each endpoint |
| `unit-test-result.json` | Test run results for unit tests |
| `integration-test-collection.json` | Postman collection with end-to-end flow tests |
| `integration-test-result.json` | Test run results for integration flows |

---

## API Under Test

All collections in this portfolio test the free public REST API provided by **[restful-api.dev](https://restful-api.dev/)**.

| Detail | Value |
|--------|-------|
| Base URL | `https://api.restful-api.dev` |
| Resource | `/objects` |
| Auth Required | No |
| Purpose | Practice & portfolio — publicly available, no sign-up needed |

---

## Folder Structure

```
Postman - Portfolio/
├── unit-test-collection.json       # Unit test collection (36 requests, 6 endpoints)
├── unit-test-result.json           # Unit test run result (95 passed / 40 failed)
├── integration-test-collection.json  # Integration flow collection (9 requests, 2 flows)
└── integration-test-result.json    # Integration test run result (41 passed / 0 failed)
```

---

## Unit Tests — `UNIT TEST`

Tests each endpoint individually across **Happy Path**, **Negative**, **Edge Case**, and **Business Logic** scenarios.

### Endpoints Covered

| Endpoint | # Tests | Scenarios |
|----------|---------|-----------|
| `GET /objects` | 7 | List all, filter by ID, multiple IDs, non-existent IDs, duplicates, schema & response time |
| `GET /objects/{id}` | 6 | Valid ID, null data, non-existent ID, non-numeric ID, first ID, schema validation |
| `POST /objects` | 9 | Create with data, null data, missing name, empty body, malformed JSON, special chars, long name, nested payload, auto-ID & timestamps |
| `PUT /objects/{id}` | 5 | Full replace, non-existent ID, missing name, empty data, updatedAt & response time |
| `PATCH /objects/{id}` | 5 | Partial update name, partial update data, non-existent ID, empty body, updatedAt timestamp |
| `DELETE /objects/{id}` | 4 | Delete existing, non-existent ID, double-delete, response shape & response time |

### Unit Test Result Summary

| Metric | Value |
|--------|-------|
| Status | Finished |
| Total Requests | 36 |
| Assertions Passed | 95 |
| Assertions Failed | 40 |
| Total Time | 4,696 ms |
| Run Date | 2026-04-18 |

---

## Integration Tests — `INTEGRATION TEST FLOW`

Tests end-to-end user flows by chaining multiple requests and passing data between steps using Postman variables.

### Flows Covered

**FLOW: Full CRUD** (6 steps)
1. Create a new object
2. Read the created object
3. Full replace with PUT
4. Partial update with PATCH
5. Delete the object
6. Verify deletion (GET returns 404)

**FLOW: List and Retrieve** (3 steps)
1. List all objects and extract a random ID
2. Get the object by the extracted ID
3. Filter objects by three extracted IDs

### Integration Test Result Summary

| Metric | Value |
|--------|-------|
| Status | Finished |
| Total Requests | 9 |
| Assertions Passed | 41 |
| Assertions Failed | 0 |
| Total Time | 1,382 ms |
| Run Date | 2026-04-18 |

---

## How to Import Collections

1. Open **Postman**
2. Click **Import**
3. Select the `.json` collection file
4. Run using the **Collection Runner** or via **Newman** (CLI)

```bash
# Run with Newman (CLI)
newman run unit-test-collection.json
newman run integration-test-collection.json
```
