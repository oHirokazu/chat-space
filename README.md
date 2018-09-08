# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## userテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, unique: true|
|name|text|null: false, unique: true|
|email|text|null: false, unique: true|

### Association
- has_many :groups, through: :members
- has_many :members

## groupテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, unique: true|
|name|text|null: false|

### Association
- has_many :users, through: :members
- has_many :members
- accepts_nested_attributes_for :members

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|foreign_key: true|
|image|string|foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
