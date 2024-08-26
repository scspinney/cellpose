# Google Colab Setup to Connect Local Data via Tunnel on Port 8000

This guide will help you set up a Google Colab environment that connects to your local data using `localtunnel` on port 8000. This is useful if you want to access files stored on your local machine directly from Colab.

## Prerequisites

1. **Python**: Ensure Python is installed on your local machine.
2. **Node.js and npm**: Make sure you have Node.js and npm installed on your local machine. You can install them from [nodejs.org](https://nodejs.org/). Or use brew on mac:
   ```bash
   brew install node

## Step 1: Start a Local Server

1. Open a terminal on your local machine.
2. Navigate to the directory you want to serve files from. For example:
   ```bash
   cd /path/to/your/data

3. Start a simple HTTP server on port 8000:
   ```bash
   python3 -m http.server 8000

This command will start a local HTTP server, serving files from the current directory.

## Step 2: Install localtunnel

If you haven't installed localtunnel yet, follow these steps:

1. Install localtunnel globally using npm:
   ```bash
    npm install -g localtunnel

## Step 3: Start localtunnel

1. In the terminal, run the following command to start localtunnel on port 8000:
   ```bash
   npx localtunnel --port 8000

2. After running the command, you will receive a public URL. This URL will tunnel traffic from the internet to your local server on port 8000. Example output:
   ```bash
   your url is: https://your-tunnel-url.loca.lt

## Step 4: Access Files in Google Colab
1. Open your Google Colab notebook.

2. Use the wget command in a code cell to download files from your local machine using the public URL provided by localtunnel:
   ```bash
   !wget -r -np -nH --cut-dirs=1 https://your-tunnel-url.loca.lt

Replace https://your-tunnel-url.loca.lt with the actual URL from your localtunnel session.

3. Verify the files have been downloaded by listing the directory:
   ```bash
   !ls -l
You can check how much space is left on your Google Colab server using:
   ```bash
   !df -h
