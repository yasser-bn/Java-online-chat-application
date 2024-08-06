
# Chat Application

This is a simple online chat application using Java. It consists of a server and a client that allows multiple users to communicate with each other in real-time. Each user is assigned a unique ID when they connect to the server, and their messages are broadcasted to all other connected users with their user ID as a prefix.

## Features

- Multi-threaded server that can handle multiple clients simultaneously.
- Unique user ID assigned to each client upon connection.
- Messages are prefixed with the sender's user ID for clarity.
- Prevention of duplicate message sending from the same client.

## Prerequisites

- Java Development Kit (JDK) installed on your system.
- Basic knowledge of Java and networking concepts.

## How to Run

### 1. Compile the Source Code

First, compile both the server and client Java files. Open a terminal or command prompt and navigate to the directory containing the source files. Then, run the following commands:

```bash
javac ChatServer.java
javac ChatClient.java
```

### 2. Start the Chat Server

To start the server, execute the following command:

```bash
java ChatServer
```

This will start the server on port `12345` and listen for incoming client connections. The server will display messages when clients connect or disconnect and when messages are received.

### 3. Start the Chat Clients

To start a client, open another terminal or command prompt, and run the following command:

```bash
java ChatClient
```

You can start multiple clients in separate terminal windows to simulate multiple users. Each client will be assigned a unique user ID upon connecting to the server.

### 4. Send and Receive Messages

- Once connected, type messages into the client terminal and press `Enter` to send them.
- Messages sent by other users will appear in the client terminal, prefixed with the sender's user ID.
- Duplicate messages from the same client are not allowed.

## Implementation Details

### ChatServer.java

- **ConcurrentMap**: Used to store client connections using `ConcurrentHashMap` to handle concurrent access.
- **ClientHandler**: A runnable class that handles communication with each connected client. It listens for incoming messages and broadcasts them to other clients.
- **broadcastMessage**: A method to send a message to all connected clients except the sender.

### ChatClient.java

- **ReceivedMessagesHandler**: A runnable class that listens for incoming messages from the server and displays them unless they are from the current user.
- **sendMessage**: Sends messages to the server. Prevents sending the same message consecutively.

## Notes

- Ensure that the server is started before launching clients.
- The server and clients must be run on the same machine or network. Adjust the IP address in `ChatClient.java` if running on different machines.

## Troubleshooting

- If you encounter a `BindException`, ensure that the port `12345` is not in use by another application.
- If clients cannot connect, verify the server is running and check network connectivity.
