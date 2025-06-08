# ICT171 Cloud Server Project 👨‍💻
Creativity Art Gallery

As part of the ICT171 - Introduction to Server Environment project, I developed a cloud-based portfolio website called Creativity Art Gallery, which is explained in this GitHub repository.

This project's main goal was to set up a web server using AWS EC2 manually, configure it with Apache, link a custom domain from Hostinger, and secure the website using HTTPS with an SSL certification from Certbot.

Step-by-step procedure & Commands<br><br><br>
***Step 01 : Launch EC2 Instance (Ubuntu)***

1. Platform: Log in to the AWS Console http://aws.amazon.com/ec2/

2. Click "Launch Instance" to start the process of creating a new virtual machine 
3. Name the Instance   - Example ict171_server
4. Select the Instance Type Ubuntu server 24.04 LTS (free tier eligible)
5. Configure Key Pair
    - Make a new key pair if you don't already have one (ict171.pem)
    - Save it safely after downloading it, you will need it to connect later.
6.  Set Network Settings
    - 🔘 Create a security group
    - ✅ Allow SSH traffic from
    - ✅ Allow HTTPS traffic from the internet
    - ✅ Allow HTTP traffic from the internet
7. Leave the default storage and advanced settings.
8. Click "Launch Instance"
9. Select your instance as soon as the running instance status appears & click the **connect** button.

Afterwards, under SSH client, you will find the command to connect via terminal, and you can also copy your IPv4 address to connect and view your website later.<br><br><br>

***Step 02: Connect to EC2 via SSH***

Once your instance is running, use SSH to connect to it—a safe way to connect to the server from a distance.

Open your terminal (Windows CMD / Ubuntu WSL / Terminal app) and type the command by replacing your public IP address (IPv4 of your EC2)
<pre> ssh -i ict171.pem ubuntu@your-public-ip </pre>

🎉 Now you have successfully connected to your cloud server terminal !<br><br><br>

***Step 03: Install Apache Web Server***

The program Apache transforms your server into a web server, enabling us to access your website using a browser.

First, update the system,
<pre>sudo apt update</pre>
Then install Apache,
<pre>sudo apt install apache2</pre><br><br>
***Step 04: Upload a Unique HTML Website***

You can add your HTML code or make changes to the default page.
<pre>sudo nano /var/www/html/index.html</pre>
⭕ Use (ctrl + o to save) & (ctrl + x to exit)<br><br><br>

***Step 05: Purchase a Domain Name***
- I used Hostinger to buy a domain name as creativityartgallery.art
- A domain name is easier to remember than an IP address and conveys a professional image.<br><br><br>


***Step 06: Update DNS Records***
- Create DNS records to connect your domain name to your EC2 server
- You could do this under your Hostinger DNS settings.

New records
- <pre>A Record |  @  | Public IPv4 (54.87.128.241)</pre>
- <pre>CNAME    | www | creativityartgallery.art</pre>

🌐 **Test** to verify that the records have been updated accurately, use https://dnschecker.org/<br><br><br>

***Step 07: Use the Snap Package Manager to install Certbot***

Certbot is used to install and obtain SSL certificates & certbot is installed using snap.

- Install Certbot,
<pre>sudo snap install core
sudo snap refresh core
sudo snap install-- classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot</pre>

- Run Certbot
<pre>sudo certbot --apache</pre>
This command,
- Request an SSL certification
- Update your Apache configuration automatically
- Enables your website to use HTTPS
  
🎉 Congratulations! You have successfully enabled https on your domain.<br><br><br>

***Step 08: Testing Time***

Check your domain

<pre>https://creativityartgallery.art
https://www.creativityartgallery.art</pre>
To verify that your SSL certificate is active and that your website is safely using HTTPS, check the padlock icon 🔒 in your browser's address bar.<br><br><br>
 

***Step 09: Conform Firewall (Security Group) Settings***

Verify that the following inbound rules are permitted to guarantee that your server and website are reachable.

AWS EC2 ➡️ Security Groups ➡️ Inbound Rules 

<pre>Port 22 (SSH) - for secure terminal access
Port 80 (HTTP) - for regular website access
Port 443 (HTTPS) - for secure website access</pre><br>

▪️  The cloud based portfolio website is now completely operational, safe with HTTPS, and accessible through the domain.  
▪️  ICT171 Cloud Web Server Project is completed and live on the internet.
