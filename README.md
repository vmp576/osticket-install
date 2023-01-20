<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- [Exercise Files](https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/gWyavif.png" height="70%" width="70%" alt="Virtual Machine Configuration"/>
</p>
<p>
First, we will need to create our virtual machine in Azure. You must create a Resource Group and create a Virtual Machine inside of that Resource Group. The image above is similar to when you will configure a Virtual Machine. After creating your resources in Azure, you will need to connect to the Virtual Machine through Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/42xvJ11.png" height="70%" width="70%" alt="Enable IIS/CGI"/>
</p>
<p>
After connecting to your virtual machine, you will need to enable CGI
</p>
<ul>
  <li>Open up control panel</li>
  <li>Type "turn on windows features" in the search box and click the "Turn Windows features on or off" link</li>
  <li>Expand "Internet Information Services > Expand "World Wide Web Services" > Expand "Application Development Features" > And Click to Enable CGI</li>
</ul>

<p>
<img src="https://i.imgur.com/bU17iob.png" height="70%" width="70%" alt="Install PHP Manager"/>
</p>
<p>
From the Exercise Files link, download both install PHP Manager for IIS and the Rewrite Module(rewrite_amd64).
</p>

<p>
<img src="https://i.imgur.com/rRJ7l9s.png" height="70%" width="70%" alt="Create PHP Folder"/>
</p>
<p>
Then, navigate to your 
  directory and create a folder for PHP. In most cases your folder should be in C:\PHP
</p>


<p>
<img src="https://i.imgur.com/dzymTqV.png" height="70%" width="70%" alt="Extract into C:\PHP"/>
</p>
<p>
Afterward, download the compressed PHP file (php-7.3.8) and extract its contents into the C:\PHP folder. After that, download and install VC-redlist.
</p>

<p>
<img src="https://i.imgur.com/L6reDQc.png" height="70%" width="70%" alt="Install MySQL"/>
</p>
<p>
Next, install MySQL. Select a typical setup type, standard configuration. Your credentials should be Username: root and setup Password: Password1
</p>

<p>
<img src="https://i.imgur.com/5j2eUXW.png" height="70%" width="70%" alt="Register PHP"/>
</p>
<p>
Next, we will register PHP within IIS. Open up the search bar and type IIS and run it with administrator privileges. Once you are in the IIS Manager, click on PHP Manager and click the "Register new PHP version" link. Navigate to the C:\PHP folder and select the php-cgi application and hit OK.
</p>

<p>
<img src="https://i.imgur.com/YmQSzWi.png" height="70%" width="70%" alt="Upload Folder to wwwroot"/>
</p>
<p>
Now, we will start installing osTicket. Go back to the Exercise Files link and download the osTicket zip file. Open the zip file and right-click the Windows tab and open it into another Windows Explorer window. Navigate to the C:\inetpub\wwwroot folder and extract the contents of the osTicket zip file's "upload" folder into the "wwwroot" folder. Finally, rename the "upload" folder to "osTicket"
</p>

<p>
<img src="https://i.imgur.com/mAQRhB7.png" height="70%" width="70%" alt="Open osTicket installer"/>
</p>
<p>
Navigate back into the IIS manager and click on Sites>Default Web Site>osTicket on the sidebar. After selecting the osTicket folder, click on "Browse *:80" on the right-hand sidebar. It should open the osTicket installer.
</p>


<p>
<img src="https://i.imgur.com/ExxT2OX.png" height="70%" width="70%" alt="Enable PHP extensions"/>
</p>
<p>
Go back into the IIS manager and open up the PHP manager > "Enable or disable extension" link. You must enable the "php_imap.dll", "php.intl.dll", and "php_opcache.dll" extensions. After that, navigate back into the Microsoft Edge browser and refresh the osTicket installer. You should notice that some of the recommended extensions are now checked.
</p>

<p>
<img src="https://i.imgur.com/VTAGLUm.png" height="70%" width="70%" alt="Rename OST Config"/>
</p>
<p>
Navigate back to the wwwroot folder and go into C:\inetpub\wwwroot\osTicket\include and rename C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php. After that, modify ost-config's permissions such that everyone has full access to the file. To do so, navigate to the file's properties, click on "Advanced" in the "Security" tab, click "Remove Inheritence" and delete all inherited permissions, and add permissions to Everyone by selecting Everyone in the "Principle" link.
</p>

<p>
<img src="https://i.imgur.com/VTAGLUm.png" height="70%" width="70%" alt="Rename OST Config"/>
</p>
<p>
Navigate back to the wwwroot folder and go into C:\inetpub\wwwroot\osTicket\include and rename C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php. After that, modify ost-config's permissions such that everyone has full access to the file. To do so, navigate to the file's properties, click on "Advanced" in the "Security" tab, click "Remove Inheritence" and delete all inherited permissions, and add permissions to Everyone by selecting Everyone in the "Principle" link.
</p>

<p>
<img src="https://i.imgur.com/gQxo10J.png" height="70%" width="70%" alt="Rename OST Config"/>
</p>
<p>
Now we will continue setting up osTicket. For the settings, you can write anything down but I recommend that you write those down in case you will need them in the future. As for your Admin User, I recommend that you set up the properties as - First Name: User, Last Name: Admin, Email: user.admin@admin.com, Username: user.admin, Password: Password1.
</p>


<p>
<img src="https://i.imgur.com/yKT1sNu.png" height="70%" width="70%" alt="Configuring Heidi SQL"/>
</p>
<p>
Before we proceed, we will need to install Heidi SQL. Download and install Heidi SQL from the exercise files. After launching Heidi SQL. Click "New" and enter User: root Password: Password1 and hit Open.
</p>

<p>
<img src="https://i.imgur.com/xkioIQg.png" height="70%" width="70%" alt="Finalizing osTicket Setup"/>
</p>
<p>
Go back into the osTicket installer and enter MySQL Username: root and MySQL Password: Password1. Go back into Heidi and create a new database called osTicket. Finally, type osTicket into the MySQL Database in the osTicket Installer and hit Install Now.
</p>

<p>
<img src="https://i.imgur.com/GaU35Qu.png" height="70%" width="70%" alt="Clean Up"/>
</p>
<p>
One last thing in order to clean up. Delete the c:\inetpub\wwwroot\osTicket\setup folder and set the C:\inetpub\wwwroot\osTicket\include\ost-config.php file permissions for Everyone to Read Only.
</p>
