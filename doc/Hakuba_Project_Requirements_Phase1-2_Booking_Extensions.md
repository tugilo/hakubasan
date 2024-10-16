---
marp: true
theme: default
paginate: true
style: |
  section {
    background-color: #fff;
    font-family: "Hiragino Sans", "Meiryo", sans-serif;
    font-size: 20px;
  }
  h1 {
    color: #0066cc;
    font-size: 28px;
  }
  h2 {
    color: #0066cc;
    font-size: 24px;
  }
  h3 {
    font-size: 20px;
  }
  .company-info {
    position: absolute;
    bottom: 60px;
    right: 40px;  
    text-align: right;
    font-size: 24px;
    color: #0066cc;
  }
  .date {
    font-size: 18px;
  }
---

# 白馬館プロジェクト要件整理

<div class="company-info">
  アデリープランニング株式会社<br>
  <span class="date">2024年10月10日</span>
</div>

---

# 宿泊予約システム要件

## 1. 宿泊予約の変更機能
- **日付変更・人数変更**が必要。キャンセル＆リブックを避ける設計。
- **バックエンド処理**として、自動キャンセルと再予約プロセスを吸収し、ユーザーにシームレスな体験を提供。
- 利用者には一貫した「変更完了」だけが表示され、リソース管理は自動化。

## 2. リブック防止機能
- **既存予約の変更を優先**し、キャンセルプロセスを極力避ける。
- バックエンドでの処理は自動化し、顧客が再予約プロセスを意識することなく予約変更を完了できる。

---

## 3. 緊急対応とオーバーブッキング
- 山小屋の特性を考慮し、予約が**100％を超えても柔軟に対応**するシステム設計。
- **避難所機能**を備え、トラブルや体調不良により系列宿泊施設へ移動可能にする。
- オーバーブッキング時も、リソース（食事、サービス）を効率的に管理し、対応可能な体制を整える。

## 4. QRコードによるチェックイン・チェックアウト
- 宿泊施設での迅速な手続きを可能にするため、**QRコード**を利用してチェックイン・チェックアウトを実装。

---

# アクティビティ予約システム要件

## 1. 利用者の希望日時取得と対応
- **第一希望～第三希望**までの日時を取得し、施設側で対応可能な日程を選択。
- カレンダー機能を実装し、施設の空き状況を視覚的に表示。

## 2. カレンダー・メッセージ機能
- 施設と利用者間での**メッセージ機能**を活用し、予約変更や確認を容易に。
- **カレンダー**で予約状況を確認し、変更を簡単に行えるインターフェース。

---

# キャンセルポリシーと予約変更可能日時

## 1. キャンセルポリシー
- 予約のキャンセルに関する取り決めを実装。**キャンセル料**やキャンセル期限を設定。
  - 例: 宿泊予定日の**3日前までは無料キャンセル**、それ以降はキャンセル料が発生。

## 2. 予約変更可能日時の設定
- **予約変更の期限**を明確に設定し、変更できるタイミングを柔軟に調整。
  - 例: **宿泊予定日の2日前まで日付や人数の変更が可能**。

---

# エクステンション要件

## 1. Magetop Booking and Reservation (Premiumプラン)
　https://www.magetop.com/magento-2-booking-reservation-extension.html
- **機能**: 宿泊予約の変更が可能で、日付変更がキャンセル&リブックを必要とせず実行可能。
- **複数日予約対応**: この機能を活用し、顧客が第一〜第三希望の日程を選び、管理者が調整することが可能。また、この機能は**アクティビティの仮予約**にも応用できる。
- **日付変更**: システムがバックエンドで処理を吸収し、予約変更をスムーズに行える。

## 2. Amasty Booking and Reservation (現在開発中)
　https://amasty.com/booking-system-for-magento-2.html
- **機能**: 複数の予約タイプ、カレンダー管理、プロモーション設定。
- **日付変更**: 見た目では変更可能だが、バックエンドではキャンセル&リブックになる可能性が高い。

---

## 3. Webkul Booking & Reservation
　https://store.webkul.com/magento2-booking-reservation.html
- **機能**: 宿泊、レンタル、イベント管理。予約カレンダーや割引設定が可能。
- **日付変更**: 標準対応なし。カスタマイズが必要。

## 4. Magenest Booking and Reservation
　https://store.magenest.com/magento-2/booking-and-reservation.html
- **機能**: 宿泊やレンタル、イベント予約管理、カレンダー機能を提供。
- **日付変更**: キャンセル&リブックが必要な場合があるが、カスタマイズで変更可能。

## 5. Milople Booking & Reservation
　https://www.milople.com/magento-2-booking-reservation.html
- **機能**: 複数日予約、リソース管理、通知機能。
- **日付変更**: 見た目は可能だが、バックエンドではキャンセル&リブックの処理。

---

# 総括

- **Magetop Booking and Reservation Premiumプラン**が予約変更機能と複数日予約対応をサポートしており、要件に最適な選択肢となる。
- **日付変更と人数変更機能**がクライアントにとって重要で、システムでの自動化プロセスを吸収する設計が必要。
- **複数日予約機能**は、アクティビティの仮予約にも応用でき、管理者が希望日程を調整するシステムを構築可能。
- **キャンセルポリシー**や**予約変更可能日時**のルール設定が不可欠。エクステンション選定時にカスタマイズの可能性を重視する。