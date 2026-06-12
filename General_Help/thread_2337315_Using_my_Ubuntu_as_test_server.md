---
title: "Using my Ubuntu as test server"
date: 2016-09-16
forum: General Help
---

### Post by tonma on 2016-09-16
Hello,

I would like to build a website and test it in my network, and I have a few questions:

- I only have 1 laptop, is it possible to use it both as developing and server machine the same time?
- I guess that in any case, I will need to setup LAMP on my Ubuntu (I am using 16.04 LTS, Not server version, because I want a GUI for development, in case I can do both on the same laptop): There are so many tutorials out there on how to setup my PC as a local server, with each tutorial has the same main installation instructions, but many different extra changes that are confusing for me as a beginner. I would really like you to link me to the best most up-to-date tutorial you think is available for my usage: mainly use my laptop as testing for the website I am building, which will include some databases

I know it might be for more advanced users, but I already have some experience and I want to expand the knowledge, even if it won't work for the first time

Thanks

---

### Post by HermanAB on 2016-09-16
I would suggest that you install Virtualbox and make a test server in there.  It is usually best not to mess up your daily use machine with test software.  Using a virtual machine, means that you can experiment to your heart's content.

---

### Post by ian-weisser on 2016-09-16
You can use the same system for a desktop and server at the same time...but it's a terrible idea without a few precautions. The first time you get hacked (your first learning server WILL get hacked!), all your personal data is compromised.

Use a Virtual Machine for your learning server. Several excellent VM host applications are in the Ubuntu Repositories. Install Ubuntu Server on the VM.

Basic security habits. Start these from day one:
- Don't mix missions. One VM for webserver. Another VM for fileserver. Another VM for backup server. Keep each super simple.
- Do NOT install internet-facing server applications on the host system. Use the VM. The VM protects you.
- Learn to use SSH keys instead of passwords. Use SSH keys every time. NEVER operate any server using mere passwords. The bad guys *will* find it and penetrate it.
- Audit your open ports and logs on a regular basis.
- Versioned backups. Systems crash or get compromised all the time (hello, database exploits!). Be prepared to rebuild with good notes and good backups.


Once you have made all your mistakes in the VM, then you are ready to replicate on a VPS or Container or whatever production environment you wish.

---

### Post by Habitual on 2016-09-16
Docker+Wordpress in less than 5 minutes...

Shout if that interests you.

---

### Post by tonma on 2016-09-17
> **HermanAB said:**
> I would suggest that you install Virtualbox and make a test server in there.  It is usually best not to mess up your daily use machine with test software.  Using a virtual machine, means that you can experiment to your heart's content.

> **ian-weisser said:**
> You can use the same system for a desktop and server at the same time...but it's a terrible idea without a few precautions. The first time you get hacked (your first learning server WILL get hacked!), all your personal data is compromised.

Use a Virtual Machine for your learning server. Several excellent VM host applications are in the Ubuntu Repositories. Install Ubuntu Server on the VM.

Basic security habits. Start these from day one:
- Don't mix missions. One VM for webserver. Another VM for fileserver. Another VM for backup server. Keep each super simple.
- Do NOT install internet-facing server applications on the host system. Use the VM. The VM protects you.
- Learn to use SSH keys instead of passwords. Use SSH keys every time. NEVER operate any server using mere passwords. The bad guys *will* find it and penetrate it.
- Audit your open ports and logs on a regular basis.
- Versioned backups. Systems crash or get compromised all the time (hello, database exploits!). Be prepared to rebuild with good notes and good backups.


Once you have made all your mistakes in the VM, then you are ready to replicate on a VPS or Container or whatever production environment you wish.

Thanks guys! The problem I have a very weak system, with only 4GB ram (and a laptop CPU). I will though give it a try. Since I am quite new to Ubuntu, is there any tutorial on how to install the VM and Ubuntu server, and then, as ian-weisser said, where is the stage where I need to use SSH instead of password? I will see this option while installing Ubuntu server inside the VM? (It will ask me to use SSH or password?)


> **Habitual said:**
> Docker+Wordpress in less than 5 minutes...

Shout if that interests you.

I would like to give a try to everything that might work. What is it exactly?

---

### Post by ian-weisser on 2016-09-17
You should not need a tutorial to install a VM host on Ubuntu. You have Ubuntu Software Center.
You should not need a tutorial on how to download an Ubuntu Server 16.04 .iso. Simply remember where you save it, so you can tell the VM host where to find it.
You should not need a tutorial on how to install Ubuntu into a new guest VM. Most VM host applications have a 'New VM' walkthrough.

---

### Post by tonma on 2016-09-17
> **ian-weisser said:**
> You should not need a tutorial to install a VM host on Ubuntu. You have Ubuntu Software Center.
You should not need a tutorial on how to download an Ubuntu Server 16.04 .iso. Simply remember where you save it, so you can tell the VM host where to find it.
You should not need a tutorial on how to install Ubuntu into a new guest VM. Most VM host applications have a 'New VM' walkthrough.

That shouldn't a problem then, but where is the stage where I choose to log into the server with SSH instead of password?

---

### Post by HermanAB on 2016-09-17
4GB is enough for 4 to 6 VMs running simultaneously

---

### Post by tonma on 2016-09-17
> **HermanAB said:**
> 4GB is enough for 4 to 6 VMs running simultaneously

Thanks, I noticed that also Ubuntu server is not so demanding on hardware, so everything is OK.
but I've reached the stage where I downloaded PuTTY from Windows in order to connect to the server (Using Windows instead). 
The problem is it gives me Software caused connection abort. I looked at the official Ubuntu documentation on how to configure SSH: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
It tells to configure the [COLOR=#333333][FONT=UbuntuMono]sshd_config[/FONT][/COLOR] file. I just don't know what should be in there, there is too much to edit. (I'm using nano to edit)

How should i edit the sshd_config to be able to connect from PuTTY to the server. 

Also, why when I type ifconfig on the Ubuntu server, I get a different inet addr than my local router's ip?

**EDIT: After updating everything, and changing stuff on VirtualBox settings, the ip has changed, and when I connect to the ip I get to "Apache2 Ubuntu Default Page", instead of the OpenSSH server.
I do want to use it also as Apache, but does that mean I can't use a SSH connection to it? Why it doesn't give me the option to set up SSH? Guys I know I may be mixing some things, but please go easy on me, I'm just at the beginning of this. My goal is to create a server to test a website and send information from the website to the server (user id, passwords, etc) using MySQL tables, and then view the tables on the server (if possible?)

> **ian-weisser said:**
> You can use the same system for a desktop and server at the same time...but it's a terrible idea without a few precautions. The first time you get hacked (your first learning server WILL get hacked!), all your personal data is compromised.

What do you mean it will get hacked ? :o
And I just can't find any good explanation on how to login with SSH. So confusing. I made 1 VM as you said for Apache2, but how to login to SSH? (When installing the Ubuntu server, I also ticked the option to install it as SSH server, but.. what's next?)

---

### Post by ian-weisser on 2016-09-17
Configure SSH Server on the VM using [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring). For your very first try, keep passwords enabled.
Configure networking on your VM host application so the two machines can see each other. 
Login from the host system to the guest VM using ssh (password).

Now you know ssh works.
Go back into the VN guest and disable passwords forever using [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
Generate and share a key to the VM guest using [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys). Share the key to the VM host.
Login from the host system to the guest VM using ssh (keys).

Now you know ssh + keys work.

---

### Post by tonma on 2016-09-18
I followed these steps:

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

[COLOR=#333333][FONT=Ubuntu]You will be prompted for a location to save the keys, and a passphrase for the keys. This passphrase will protect your private key while it's stored on the hard drive:[/FONT][/COLOR]

Generating public/private rsa key pair.
Enter file in which to save the key (/home/b/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/b/.ssh/id_rsa.
Your public key has been saved in /home/b/.ssh/id_rsa.pub.

but I accidentally gave a name when it asked me this: "Enter file in which to save the key (/home/b/.ssh/id_rsa):" I wrote 'mypublickey' and pressed Enter. Now it told me instead of 'Your public key has been saved in /home/b/.ssh/id_rsa.pub',
'Your public key has been saved in mypublickey' .. How do I start over, and delete my previous attempt? Or I just re-do everything and it will over write the old dir and files?

**Also, how can I view the keys? I tried typing 'sudo nano /home/b/.ssh/id_rsa' or 'sudo nano /home/b/.ssh/mypublickey' but it just creates new files and doesn't open the file where the key is stored?

Ty

---

### Post by ian-weisser on 2016-09-18
You can use 'mv' to rename 'mypublickey' to '[COLOR=#000000]/home/b/.ssh/id_rsa.pub[/COLOR]'
Or you can merely delete the relevant files to start over.
Keys are just text files used very cleverly.

Don't use sudo for user-level actions, like opening a text file that 'b' already owns. Simply use 'nano'

---

### Post by DrRus on 2016-09-18
tonma - I'm not saying that running local server is a bad idea, but I think you went the hard way with this. 
If you just want to test your site locally, you may want to look into [XAMPP]("https://en.wikipedia.org/wiki/XAMPP").

(If you want to do some real-life testing, or just mess around with a server on the internet, I recommend getting a small cloud server; I use DigitalOcean, which is dirt cheap, $0.007/hour, but there are tons of others.[URL="https://en.wikipedia.org/wiki/XAMPP"])
[/URL]

---

### Post by coldraven on 2016-09-18
Loads of free, ready-made  VirtualBox server images here. Just make sure to change the passwords :)
[https://virtualboxes.org/images/]("https://virtualboxes.org/images/")

Edit: This 2009 dual-core laptop with 4GB of memory can easily run a VBox server and VBox Windows XP

---

### Post by tonma on 2016-09-18
> **ian-weisser said:**
> You can use 'mv' to rename 'mypublickey' to '[COLOR=#000000]/home/b/.ssh/id_rsa.pub[/COLOR]'
Or you can merely delete the relevant files to start over.
Keys are just text files used very cleverly.

Don't use sudo for user-level actions, like opening a text file that 'b' already owns. Simply use 'nano'

Thanks, I realized that, my experience with Linux is not that great to try and create my own server, and the following post by DrRus was exactly what I was going to ask:

> **DrRus said:**
> tonma - I'm not saying that running local server is a bad idea, but I think you went the hard way with this. 
If you just want to test your site locally, you may want to look into [XAMPP]("https://en.wikipedia.org/wiki/XAMPP").

(If you want to do some real-life testing, or just mess around with a server on the internet, I recommend getting a small cloud server; I use DigitalOcean, which is dirt cheap, $0.007/hour, but there are tons of others.[URL="https://en.wikipedia.org/wiki/XAMPP"])
[/URL]

DrRus, Thank you! I was just about to ask whether I can use Ubuntu like I'm using WampServer in Windows, instead of creating a real server. So I will create only a test server in a desktop Ubuntu rather than using Ubuntu Server. But, instead of using XAMPP as a bundle, Can I use a local test by installing MySQL, Apache2 and PHP separately on Ubuntu? Or that's more complicated? (talking about testing my webpages locally) **edit: I found an explanation and I now have it working, Thanks!


**In the tutorial I found, it always mentions securing the server. But since I use it on localhost, is there still a need in securing?

---

### Post by DrRus on 2016-09-18
Sorry I've only used XAMPP on Windows and I'm pretty nooby with Linux myself, but I'm glad you got it working.

You shouldn't have security issues running local, but better safe than sorry ;)

---

### Post by ian-weisser on 2016-09-18
> **tonma said:**
> But since I use it on localhost, is there still a need in securing?

Need depends on if your localhost is secure.
Many of the security gurus in this forum will tell you that security is a set of good habits. "I created a server, I lock it down as part of the setup *every* time."
Good security practice, like regular moderate exercise or good nutrition, surely cannot hurt. Professionals cultivate those good habits.

---

### Post by tonma on 2016-09-19
> **DrRus said:**
> Sorry I've only used XAMPP on Windows and I'm pretty nooby with Linux myself, but I'm glad you got it working.

You shouldn't have security issues running local, but better safe than sorry ;)

> **ian-weisser said:**
> Need depends on if your localhost is secure.
Many of the security gurus in this forum will tell you that security is a set of good habits. "I created a server, I lock it down as part of the setup *every* time."
Good security practice, like regular moderate exercise or good nutrition, surely cannot hurt. Professionals cultivate those good habits.

Thank you guys for your help!

Ian-weisser, I hope I'm not going off topic, but, do you have any place I can see how to secure my home network? I'd like to practice those habits as you said

---

### Post by ian-weisser on 2016-09-19
There are many, many threads discussing good habits in this forum.

---

### Post by tonma on 2016-09-26
> **ian-weisser said:**
> There are many, many threads discussing good habits in this forum.

Ian,

I was now wondering:

You said that my first test server WILL get hacked. But then I saw hosts such as DigitalOcean, which you pay for a virtual machine and IP, but create the server yourself, so it is actually both a test and a real server. What if I choose to use their service? How can I use it the first time and not get hacked? I mean, are there auto attacks just looking for easy places to hack? Or how does that work?

---

### Post by ian-weisser on 2016-09-26
Everyone's first server is the one they make all the first-timer mistakes on. Might be leaving ssh open to a dictionary attack, might be installing unnecessary bloatware that causes sluggishness, might be a dodgy VPS provider with flaky service and no support.

Nobody drives a car perfectly the first time they try.
Nobody swims perfectly the first time they try.
Nobody spins up a server perfectly (including good security habits) the first time they try.

Once you have a live server, check your inbound connection attempts. Yes, there are lots of bot out there doing nothing but probing randomly, endlessly, for vulnerabilities to exploit. And they find those vulnerabilities often enough to make their effort worthwhile.

---

