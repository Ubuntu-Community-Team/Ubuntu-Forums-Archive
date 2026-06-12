---
title: "Apache web server root folder and passwords"
date: 2007-10-09
forum: General Help
---

### Post by RudolfMDLT on 2007-10-09
Hi there,

I've setup a apache server and a DynDNS account and it works well in principal. What I would like is to now link what is in the /var/www folder to my "MyDocuments" folder so that I can access my work from varsity and friend's houses. Can I setup shortcuts as hyperlinks?

Secondly, is it possible to force and require a login in order to see the page - I don't want random people snooping around in my folders!? :)

Thanks for any help,

Rudolf Hoehler

---

### Post by dfreer on 2007-10-09
you can do this:
```
sudo ln -s ~/Desktop/MyDocuments /var/www/
```
The Folder will now show up like so:
[http://yoursite.dyndns.org/MyDocuments/](http://yoursite.dyndns.org/MyDocuments/)
Just make sure the MyDocuments folder is readable by everyone so that you can access it from the website.

As for create a login, it's very much possible, just don't ask me how ;) I believe for you the eaisest way would probably use an .htaccess file to require a login.

---

### Post by RudolfMDLT on 2007-10-09
Thanks a lot! :) Its works perfectly! :)

Noob: I cant find the security file you specified? Could some one else maybe help me out here with the password thing!?

Thanks a lot!

Rudolf

---

### Post by kelbizzle on 2007-10-09
There you go "The comprehensive guide to .htaccess "

[http://www.javascriptkit.com/howto/htaccess.shtml](http://www.javascriptkit.com/howto/htaccess.shtml)

---

### Post by RudolfMDLT on 2007-10-11
#-o What? Okay - I read the tutorial, and I have created an hraccess file in /var/www. but it doesn't work. The tutorial doesn't say whether I should tell apache that it is there or to use it... should it just work by pasting it in a folder?

Please help me clear this up! :)

Thanks,

Rudolf

EDIT: How do I check whether a text file is ASCII or BINARY? How do I save a file as either using nano or kate? I used to use notepad ages ago and it gave the encoding options at the save prompt if I remember correctly.

---

### Post by dfreer on 2007-10-11
As for the text file issue, most text editors should automatically save the files as ASCII characters I do believe, I've never worried about it myself. When you use nano, at the bottom it has a list of commands, one of which is the "^X Exit". Hit <Ctrl>+X to save and quit.

Ok, lemme grab some books and lookup how to use the .htaccess file.

EDIT: Ok, the above how-to is written from a windows standpoint, and the issue of ASCII/Binary format is related to uploading files to the server from FTP. If you are doing this your server directly, you don't need to worry about it. You should be able to just write the file, and place it where it needs to go. Remember, the .htaccess file should go IN the directory you are trying to secure, and the password file should not be anywhere in /var/www/

This guide is pretty much the same as the above link, but it might help you a little more if you are having problems.
[http://httpd.apache.org/docs/2.2/howto/auth.html#theprerequisites](http://httpd.apache.org/docs/2.2/howto/auth.html#theprerequisites)

---

### Post by RudolfMDLT on 2007-10-12
thanks dfreer! ht files proved a headache and I'm now using http.conf - that guide really helped! Thank you very much!

Now:

Can I and if so, how do I create a hyperlink across a network. That is, can I create a hyperlink from the machine that is hosting to a folder on my pc?

Thank you very much! You guys have really helped me out of the fog here! :P

Cheers,

Rudolf

---

### Post by dfreer on 2007-10-12
Glad to help! ok, now I'm a bit confused about what you want to do now. So I'm guessing this is what you want to do:

From your linux laptop anywhere on the internet, be able to open your documents on the linux server at home and modify them or create new ones. In this case, I'd probably use SSH and use "Places > Connect to Server..." on the linux laptop. It will place a folder on your desktop, and you will be able to manage the files "almost" exactly as if they are really on your desktop.

From a windows machine, you can use this SSH client (I prefer it over PuTTy for file transferring):
[http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html](http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html)
Specifically:
[http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe](http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe)
This will work pretty much the same way as an FTP client, only it'll be using SSH to encrypt traffic.

---

### Post by RudolfMDLT on 2007-10-13
Not what I want to do - but very good advice none the less! :)  Which I may need to take into account over what I want.

Here is what I thought - We have  5 PC's in the house, one currently running the apache server and running as a backup server for the house. Is it possible to create a Samba link accessible from the web to each machine. The reason for this is that 3 out of the 5 pc's run Ubuntu, the other 2 run XP. The purpose of the system is to be able to, on a web page, allow access to specific parts of everyone's data. The fact that the PC the central backup server makes the local content no older than a week but having direct access to each machine would be great. I thought about FTP but, as I want to host my own little website for the heck of it and only require READ access, having a webpage seemed a quick and easy way to get both done.

But now that I have re thought it - If I mount a drive of all the machines in the house, using a smbfs, and create a hyperlink in my page to each "mapped" folder, will apache or Ubuntu allow this? 

Thanks for your patients! ;) 

Rudolf

---

### Post by RudolfMDLT on 2007-10-13
Okay - I have tried to mount files via smbfs and it worked. I have even created a symbolic link to the folder in a folder that should be accessible. Now the contents of the folder is:

> root@backuppc-desktop:~# ls /var/www/filefolder/
Music  prions2.pdf  prions.pdf  stuff

But when Mozilla logs into that specific folder from the web you can only see Music - a symbolicly linked folder that is local to that machine and the two pdf files. Stuff is the network folder. Just as I thought, somewhere one or both the Ubuntu machines are not allowing networked material to be published on the web. 

Is there anyway of getting a smb mounted file system displayed on the web?

Thanks,

Rudolf

---

### Post by #Reistlehr- on 2007-10-13
look into vhosts and htpasswd..

---

### Post by RudolfMDLT on 2007-10-13
Looked into both, but I'm not sure why I should be running 2 apache servers? htpasswd.

---

### Post by dfreer on 2007-10-13
no, not 2 apache servers... vhosts. basically, it's how I run [http://packages.dfreer.org](http://packages.dfreer.org) and [http://www.dfreer.org](http://www.dfreer.org) on the same server. The problem is that you are using dydnds and don't have a domain name. You might be able to still use virtual hosts with multiple dyndns accounts, I'm not sure. But basically the whole point of this is that you can create samba shares on each machine that needs it's information on the web, mount all of those shares onto your webserver at let's say /var/www1 /var/www2 /var/www3 and so on. Then, in your /etc/apache2/sites-available/ folder, create a configuration file for each folder (let's say [http://www1.dyndns.org](http://www1.dyndns.org) [http://www2.dyndns.org](http://www2.dyndns.org)). Each family member/pc would in effect have there own website to access their data (in fact, they could very well upload some HTML files and make it their own website).

Beyond that, as long as you are mounting the samba shares correctly, I don't see why you can't mount them within the /var/www/ folder (/var/www/ubuntu1 /var/www/ubuntu2 etc), and then as long as the permissions are set right they will be able to access there stuff from your main dyndns account [http://yoursitename.dyndns.org/ubuntu1/](http://yoursitename.dyndns.org/ubuntu1/)). Symbolic links should also work, although you might need to add a line in your /etc/apache2/sites-available/000-default to tell it to follow symbolic links.

---

### Post by RudolfMDLT on 2007-10-14
That does make sense - except that I have mounted them and I can't see them! :) What  must the permissions be? I don't want to randomly go chmod 777 everything like an idiot so I'm hoping you or someone else could tell me what they should be to allow network mounts to be accessible from the web!

Thanks,
Rudolf

---

### Post by dfreer on 2007-10-15
so you can see them from within the OS, like when using nautilus, you just can't see them from the website correct? can you run the command
```
ls -l
``` on the files/folders that need to be accessed from the internet? Basically, as long as user www can read the files, they should be accessible from the internet (I'd recommend leaving the ownership of the files alone, and just make sure the files have 644 (rw-r--r--) and the folders have 755 (rwxr-xr-x) permissions. If they are symbolic links, make sure these two lines are in your /etc/apache2/sites-available/000-default file (this is mine, just ignore the other information, yours will most likely not look exactly like this):

```
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName www.dfreer.org

        DocumentRoot /data/web-root/www/
        <Directory />
**                Options FollowSymLinks**
                AllowOverride None
        </Directory>
        <Directory /data/web-root/www/>
**                Options Indexes FollowSymLinks MultiViews**
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

        # ServerSignature On


    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

You can try testing by making a link from another file/folder on the webservers filesystem to the site, to see if you can access it from the web. Also, make sure your links are symbolic:
```
sudo ln -s *yourfoldersandfiles*
```

Hopefully this helps you out!

EDIT: These might help to double-check whether you mounted your samba shares with the correct permissions (these *should* work):
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DYes.29)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

---

### Post by dfreer on 2007-10-19
Also, I don't know if this is an issue for you or not, but it's something to consider. When using Samba to share files/folders to linux machines, and those files/folders are symbolic links, you have to set an option in your /etc/samba/smb.conf to say *unix extensions = no*

---

