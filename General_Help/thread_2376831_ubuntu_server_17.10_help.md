---
title: "ubuntu server 17.10 help"
date: 2017-11-06
forum: General Help
---

### Post by jfurnas on 2017-11-06
Hey there, 

I am not sure what forum to place this question in, and couldn't find a forum specific to it, so I'll place it here. I apologize if it's not the correct place. 

I recently installed ubuntu 17.10 server, and installed Apache, MySQL and PHP on it. I am planning to use it for a staging environment for websites being developed. My current production server has CentOS7 installed with cpanel, but I believe that's overkill to use just for a staging environment. 

With that being said, I want to set up virtualhosts on ubuntu server. My plan is to host them this way:

/var/www/html <-- main serve directory
/var/www/domain.com <-- documentroot for vhost #1
/var/www/domain2.com <-- documentroot for vhost #2

each domain/account will have it's own system user, and inside of that, a symlink of /var/www/<domain> to a public_html folder. How do I set the permissions on the user or /var/www/<domain> folder so that the user can access it via the symlink, and still make it secure? I was going to use /home/user/public_html, but in doing that, I couldn't figure out how to get apache to be able to read the files in the directory successfully.

I use ubuntu 17.10 desktop every day, but it's different because I do everything from a gui, and from localhost, so I don't have much experience with setting this up this way.

---

### Post by TheFu on 2017-11-06
I wouldn't use a non-LTS for any server work.  Further, if your production server is CentOS, then you should use CentOS on your dev, test, pre-prod and DR systems too.  No need to have hassles over this when CentOS is available.

I don't think you can make a virtual webhost secure using different userids in the way you are suggesting, especially if these are webapps.  You can use a reverse proxy to connect to webapps running under the userid. It is a network socket connection so every user would run/control their own webapps and those would run on a higher port (over 1024).

Forget the GUI. Learn the shell.  [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed)   You'll need to use ssh and manage the systems over ssh anyway.

---

### Post by jfurnas on 2017-11-06
The reason I am not using CentOS 7, is for 1, I do not like how it operates. It's a very exhaustive operating system to use, especially when it's only used for staging purposes. If it weren't for having CPanel installed on it to manage virtual hosts, etc, and cpanel not having ubuntu server support, I would not be using it. I use Ubuntu desktop and command line, as well as terminal daily, so I am comfortable using the command line, and very rarely use the GUI for anything. There is also no value or gain in purchasing another cpanel license for a server that is only used between development and production to demo a site during development or just before launch.

Secondly, I know it is possible to do what I am trying to do, because many dedicated vps and webhosts use the exact same setup. CPanel even does it when it is operating, it just points to different file locations on the disk. The user is (and should) able to log into their own account and access their public_html directory, but the apache user (as well as the php user) is also able to view and serve the files using virtualhosts. It's not uncommon for it to be setup this way, and quite frankly is a much better solution than using ~userdir for apache. 

As far as managing them over SSH, I don't HAVE to. They are installed on xenserver (again, a linux distro), and I can access them from XenCenter or OpenXenManager on Linux using the console, which works the same way as SSH except it's a direct connection to the VM instead of an SSH connection.

---

### Post by TheFu on 2017-11-06
I'm familiar with how many webhosts use shared servers for many different virtual websites.  Those are not secure.  That is a dirty secret of the shared hosting world.

If you want an Ubuntu server with a similar setup to what a webhost would run, check out  [https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/2/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/2/)

Using a console over using ssh?  Urg.  ssh wins every time, IMHO.

---

### Post by jfurnas on 2017-11-06
Again, installing something like ispconfig is overkill for what this server is being used for. Doing what I originally asked is what I intend to do, whether I find the solution here or figure it out myself. 

I also disagree with your ssh>console statement. What happens when you lock yourself out of your server, or firewall rules get messed up and you can't connect to your server via SSH anymore? With xencenter console, I will NEVER have to worry about locking myself out of the server, because the console always has direct access, as if you had a physical monitor attached to the server. The only time I will ever have a problem, is if the TTY or system itself gets messed up, and if that's the case SSH won't fix it, either.

I will agree that if the server is remote, and is a physical server (not a vm), then using SSH is the way to go, but it's not ALWAYS the way to go.

---

### Post by TheFu on 2017-11-07
Over the years, I've learned to test my firewall changes for a few minutes, then undo those changes automatically.  Started doing this after locking myself out once.  Seems I wasn't the first and others had been doing it for some time.

xencenter isn't magic. Every hypervisor I know provides console access ... some over ssh. ;)  Actually, most server-class systems have a remote console capability, but that is used so seldom as to be an after thought.  OTOH, just 1 time use makes the connection worthwhile.  About once every 3 yrs, having access to the real BRS is needed.  So that does mean that technically, "ALWAYS use ssh" isn't correct.

You can use ACLs to provide the file/directory access you need.  setfacl/getfacl are the commands. Just keep the read-only parts as read-only for apache/nginx and only make the read-write areas actually read-write.  Managing ACLs across hundreds of different accounts is a hassle.  Also, you need a way for each virtual-website to request that apache be reloaded, probably by having a specific empty file in a specific location. I would limit the reload/restart to once every 5 minutes.  But if apache gets hacked, which seems likely with php webapps, all the read-write areas are vulnerable.

---

