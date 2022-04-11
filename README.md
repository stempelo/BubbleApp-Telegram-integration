# BubbleApp-Telegram-integration
Possibile architecture integration for a Bubble.io app and a bot Telegram.

``` mermaid
sequenceDiagram
    User 1->>BubbleApp: interact with app
    activate TelegramBot
    loop sync mode
            API service-->TelegramBot: logic
    end    
    BubbleApp->>+API service: request API
        rect rgb(153, 255, 205)
        API service-->DB: interact with DB
    end
    API service->>BubbleApp: response with data
    BubbleApp->> User 1: app response
    rect rgb(255, 245, 109)
        Note over TelegramBot,User 2: Inside a private chat
        loop async mode
            TelegramBot-->User 2: User interact with the bot Telegram
        end
        rect rgb(153, 255, 205)
        TelegramBot-->DB: interact with DB
        end
    end
    deactivate TelegramBot
