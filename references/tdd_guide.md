# TDD 適用性判準（TDD Applicability Guide）

本文件為郭嘉（奉孝）與徐晃（公明）的輔助參考，用於判斷一個全新專案是否應啟用測試驅動開發（TDD）。

## 核心判準

> **不查語言名單，查測試環境是否可一鍵執行。**

若主要語言具備**可在專案根目錄以單一指令執行全部測試**的標準工具，則視為 TDD 適用，應啟用。

## 常見 TDD 適用語言對照表

| 語言           | 標準測試指令                    | 備註                 |
| :------------- | :------------------------------ | :------------------- |
| Rust           | `cargo test`                    | 內建，無需額外安裝   |
| Python         | `pytest` / `python -m unittest` | pytest 為業界慣例    |
| Go             | `go test ./...`                 | 內建，無需額外安裝   |
| JavaScript     | `npm test` / `npx vitest`       | 依 package.json 設定 |
| TypeScript     | `npm test` / `npx vitest`       | 同 JavaScript        |
| Ruby           | `bundle exec rspec`             | RSpec 為業界慣例     |
| Java           | `mvn test` / `./gradlew test`   | 依建置工具而定       |
| C#             | `dotnet test`                   | 內建於 .NET SDK      |
| Kotlin         | `./gradlew test`                | 同 Java 生態         |
| Swift          | `swift test`                    | 內建於 Swift Package |
| PHP            | `./vendor/bin/phpunit`          | PHPUnit 為業界慣例   |
| Elixir         | `mix test`                      | 內建，無需額外安裝   |
| Dart / Flutter | `dart test` / `flutter test`    | 內建                 |

## 不適用 TDD 的常見情形

以下情形一律標注「本專案免除 TDD」並略過驗收基準章節：

- **純前端標記文件**：HTML、CSS 等無邏輯層的專案。
- **Shell 腳本**：bats 等工具可用，但整合成本高，非強制。
- **無測試配置的遺留專案**（非全新）：TDD 難以後置，不強制要求。
- **資料或配置類專案**：JSON schema、YAML 等無程式邏輯者。

## 奉孝的判斷流程

```text
1. 是否為「全新專案」？
   → 否 → 免除 TDD
   → 是 → 繼續

2. 主要語言是否具備可一鍵執行的測試指令？
   （參照上表；不在表中者，以「是否有 test runner」為標準自行判斷）
   → 否 → 免除 TDD
   → 是 → 在《營陣綱目》建立 § TDD 驗收基準，訂定邊界條件
```
