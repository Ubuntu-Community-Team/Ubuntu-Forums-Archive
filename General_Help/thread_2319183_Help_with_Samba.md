---
title: "Help with Samba?"
date: 2016-04-01
forum: General Help
---

### Post by david472 on 2016-04-01
Can someone direct me to the download and some help with setting up Samba on my ubuntu server/ raid system please?  I thought there was a forum for Samba, but I didn't see it.

---

### Post by SeijiSensei on 2016-04-01
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by david472 on 2016-04-02
What download file do I use?  I see the sudo to run it, but not sure which file I am supposed to run
1)  Do I run it from USB after the server is booted?
2) Do I need to download it directly to the server from a command line?

---

### Post by bab1 on 2016-04-02
> **david472 said:**
> Can someone direct me to the download and some help with setting up Samba on my ubuntu server/ raid system please? I thought there was a forum for Samba, but I didn't see it.



You should use the APT package management system to install samba.  You can use the Software Center or Synaptic (if installed) or the command line.  Do not use a downloaded .deb file to install Samba.

There is a mailing list for Samba, but it is pretty high level.  This forum is probably the best for basic advice.
> 
What download file do I use?  I see the sudo to run it, but not sure which file I am supposed to run
1)  Do I run it from USB after the server is booted?
2) Do I need to download it directly to the server from a command line?
The page that @ SeijiSensei directed you to is mainly for how to *configure Samba* not on how to install Samba.  Some of the items are not applicable to recent versions of Samba.

What are you going to use Samba for?  File sharing or Domain Control?  If you are only setting up file sharing it is pretty simple.  Just install Samba with this terminal command```
sudo apt-get install samba
```...Then you can add the share definition at the bottom of the [FONT=Courier New]**/etc/samba/smb.conf**[/FONT] file.

Here is a simple howto on configuring Samba for file sharing: [http://www.jonathanmoeller.com/screed/?p=3608]("http://www.jonathanmoeller.com/screed/?p=3608")

FYI -- If you are advised to do anything other than editing the /etc/samba/smb.conf file, **check here first!**.  Other than setting permissions or adding users you should not need to do anything to the OS for Samba to work.

---

### Post by david472 on 2016-04-03
I am using it as a video server so that people can put their video files on it and edit them from a windows machine.

---

### Post by bab1 on 2016-04-04
> **david472 said:**
> I am using it as a video server so that people can put their video files on it and edit them from a windows machine.
So all you just need to configure a file server.  I would start with the instructions I listed above.

---

### Post by david472 on 2016-04-04
Should I download Samba directly to the ubuntu server?  It has an internet connection...

---

### Post by X-RED_Tech on 2016-04-04
APT will download and install all the required packages for you (read and understand post#4) and yes, you must install it on the machine that'll be the server.

---

### Post by bab1 on 2016-04-04
> **david472 said:**
> Should I download Samba directly to the ubuntu server?  It has an internet connection...
Yes you install (which includes the download) directly to the machine you want to use as a Samba file server. Unlike Windows, where you need to download an application and then install it,  the Ubuntu OS includes an extensive  repository of applications that are downloaded and installed all with one command.

---

### Post by david472 on 2016-04-04
Ok, I perform the sudo apt-get install function.  Now I am assuming I use the nano reader/writer to
1) open the config file
2) save mapping location?
3)  Is there a certain place in the config file I need to do this?

---

### Post by bab1 on 2016-04-04
> **david472 said:**
> Ok, I perform the sudo apt-get install function.  Now I am assuming I use the nano reader/writer to
1) open the config file
2) save mapping location?
3)  Is there a certain place in the config file I need to do this?
Follow the instructions in the tutorial above. All of this is listed there.  Nano is a test editor as is VI.

Are you having problems saving the file after you edit it?  If so you need to open the file as the root user like this```
sudo nano /etc/samba/smb.conf
```

I assume you mean; where do I place the text for the file share operation? You add the share definition at the very bottom of the file.

---

### Post by david472 on 2016-04-05
Sorry, what I meant was where in the config file do I place the file location?  When I was working with ubuntu setting up the RAID, it mattered where in the config file the changes were made or if something was added in there.
Also, you said to edit the config file, but the next step in the tutorial is otherwise - just follow the tutorial instead?

Lastly, I tried to establish a password for Videoshare and it told me " Failed to add entry for user videoshare"
Does it matter about the password?  I just used a general password for now...

---

### Post by bab1 on 2016-04-05
> **david472 said:**
> Sorry, what I meant was where in the config file do I place the file location?  

What are you referring to here?  What file location are referring to?  The Samba config file (smb.conf) configures file shares of directories in this format```

[file share]
path=path/to/shared/directory
comment = description of the share (optionnal0
valid users = users able to access this share
writable = yes

```
This share definition can go at the very bottom of the smb.conf file.  Just as the tutorial says to do.
> 
When I was working with ubuntu setting up the RAID, it mattered where in the config file the changes were made or if something was added in there.

RAID configuration has nothing to do with sharing files.
> 
Also, you said to edit the config file, but the next step in the tutorial is otherwise - just follow the tutorial instead?

I'm answering your specific questions.  I thought you had read and for the most part understood the entire tutorial.  I would have followed the entire tutorial and then asked questions.
> 
Lastly, I tried to establish a password for Videoshare and it told me " Failed to add entry for user videoshare"
Does it matter about the password?  I just used a general password for now...Linux is a case sensitive 
Is there a user *videoshare*?  Is there a samba user *videoshare*?  If you are restricting the share to a specific user then passwords are very important.

---

### Post by david472 on 2016-04-06
Ok, I will be more clear this time, I can see how it was confusing before.

1) You asked me to place the "path/mapping location" in the file, correct?  Unfortunately, I am step by step kind of person and didn't look ahead at the config file - but now I see that it is just editing rather than adding to the file..

2) I created a user named videoshare using ```
**sudo smbpasswd -a videoshare**
```I was under the impression that this MADE the user name and then the password.  Maybe I am wrong.  As of now, I am the only user in the system.
If not, I need to create a user first.

-For now, I went back in and created a password for the user that is already in the system.  That worked. 
-Next I created the test directory
-tried to backup file using ```

-**sudo cp /etc/samba/smb.conf ~**
```[B]

and it gave me this error

[/B]```
 cp missing destination file operand after  /etc/samba/smb.conf~
```

---

### Post by bab1 on 2016-04-07
> **david472 said:**
> Ok, I will be more clear this time, I can see how it was confusing before.

1) You asked me to place the "path/mapping location" in the file, correct?  Unfortunately, I am step by step kind of person and didn't look ahead at the config file - but now I see that it is just editing rather than adding to the file..

Mapping is a Windows term.  This is not mapping.  You are configuring the parameters for the smbd daemon (the Samba server)  I'd suggest that when you are working with Linux configuration that you read the entire set of instructions before you start.  There are many options.  Sometimes the instructions are for a different Linux distro and won't work at all. 
> 
2) I created a user named videoshare using ```
sudo smbpasswd -a videoshare
```I was under the impression that this MADE the user name and then the password.  Maybe I am wrong.  As of now, I am the only user in the system.
If not, I need to create a user first.
You are not the only user on your system.  There are more than just the mortal users (humans).  In any event each user that is going to access shares must be both a Linux user (adduser) AND a Samba user (smbpasswd).  The Linux users can be seen with this command ```
getent passwd | grep 100
```
You can see the samba users with this command```
sudo pdbedit -L
```
> 
-For now, I went back in and created a password for the user that is already in the system.  That worked. 
-Next I created the test directory
-tried to backup file using ```

sudo cp /etc/samba/smb.conf ~
```
and it gave me this error
```
 cp missing destination file operand after  /etc/samba/smb.conf~
```
What is this test directory?  Did you make a directory in your home directory?

If you want to make a copy, you will need to declare what you are copying and what the name of the copy will be.  Like this```
sudo cp <original file name>  <copied file name>
```... source to destination.

---

### Post by david472 on 2016-04-07
[FONT=arial]Ok, thanks for your patience.  A bit of background.  
1) This is a brand new server.  I just finished installing ubuntu, brand new hard drives with a 2x 1TB RAID1 system on it. 
2) I want to create a Samba server whereas someone else on the network can log in and use the RAID drive to store video files.
2) The only user on it is myself. I ran 
```
[COLOR=#000000]sudo pdbedit -L[/COLOR]
```[COLOR=#000000] 
and only myself showed up.
3) Test directory is me following the instruction in the link you suggested for how to link for file sharing [here]("http://www.jonathanmoeller.com/screed/?p=3608") (basic Samba setup and installation by Jon Moeller

[/COLOR][/FONT]```
**mkdir /home/camalas/test**
```[FONT=arial]
[/FONT][COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]4) Copying of the config file was following the[ link]("http://www.jonathanmoeller.com/screed/?p=3608") and going step by step.

Sorry for the miscommunication on this.  I do appreciate your help.  I need to get this server up and running.[/FONT]

[/FONT][/COLOR]

---

### Post by bab1 on 2016-04-07
> **david472 said:**
> [FONT=arial]Ok, thanks for your patience.  A bit of background.  
1) This is a brand new server.  I just finished installing ubuntu, brand new hard drives with a 2x 1TB RAID1 system on it. 
2) I want to create a Samba server whereas someone else on the network can log in and use the RAID drive to store video files.
2) The only user on it is myself. I ran 
```
[COLOR=#000000]sudo pdbedit -L[/COLOR]
```[COLOR=#000000] 
and only myself showed up.
3) Test directory is me following the instruction in the link you suggested for how to link for file sharing [here]("http://www.jonathanmoeller.com/screed/?p=3608") (basic Samba setup and installation by Jon Moeller

[/COLOR][/FONT]```
**mkdir /home/camalas/test**
```[FONT=arial]
[/FONT][COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]4) Copying of the config file was following the[ link]("http://www.jonathanmoeller.com/screed/?p=3608") and going step by step.

Sorry for the miscommunication on this.  I do appreciate your help.  I need to get this server up and running.[/FONT]

[/FONT][/COLOR]
Try and understand what is being said in the tutorial.  The directory should be in YOUR home directory. The user name is ***camalas*** in the example.  You should be creating a directory mike this```
mkdir /home/<user_name>/test
```...where <user_name> is your user name.  :-)

[COLOR="#0000CD"]Edit:  My bad.  I corrected a typo in my command.  It's a / not a ?[/COLOR]

---

### Post by david472 on 2016-04-07
1) I am so new to this, so I am guessing you are asking me if I used the word CAMALAS - I did not, I used the word videoshare in its place.  See below.
```
mkdir  /home/videoshare/test
```

BUT the second question is, did I need to make a videoshare directory too?
My user is davidd, that is the only user in the system.  Should I have created something like this instead?

```
mkdir  /home/davidd/test
```

This gives me an error saying "**cannot create directory, /home/davidd/test  no such file or directory**"

---

### Post by bab1 on 2016-04-07
> **david472 said:**
> 1) I am so new to this, so I am guessing you are asking me if I used the word CAMALAS - I did not, I used the word videoshare in its place.  See below.
```
mkdir  /home/videoshare/test
```

Let's see if we can make sense of all this.  If you don't have a user named videoshare then you should NOT have a directory: [FONT=Courier New]/home/videoshare[/FONT].  When you refer to the user name in a command it is not a "word" it is know as a "term" or "variable" or an "argument".

Right now we should look at what is really in the /home directory.  Please post the output of this command```
ls -l /home
```
To preserve the fixed text formatting ost the output between [noparse]```
   
```[/noparse] blocks.  The easiest way to do that is to click on the [SIZE=5]**#**[/SIZE] icon at the top of the advanced editor that you are using to reply to this post.

Let's see what mortal users (human) exist on the system.  Post the output of this command ```
tail -n 10 /etc/passwd
```... note that there is no password in this listing so there should be no security concern.   
> 

BUT the second question is, did I need to make a videoshare directory too?
Let's see what you have right now.  Then I can advise you specifically what to do.> 
My user is davidd, that is the only user in the system.  Should I have created something like this instead?

```
mkdir  /home/davidd/test
```
This gives me an error saying "**cannot create directory, /home/davidd/test  no such file or directory**"
I'm surprised at this.  You should have been able to create a directory in your own home directory.  I can advise you better once I have seen the posted output I asked for above.

---

### Post by david472 on 2016-04-08
Ok here are the commands you asked.  I took a picture of it so hopefully that will give all the details without me omitting anything by mistake :
[IMG]http://i68.tinypic.com/21a0d48.jpg[/IMG]

---

### Post by bab1 on 2016-04-08
It is in your best interest to learn how to use the command line.  I can't highlight sections of the text to show you what is wrong or needs modifying.  Do you know how to highlight the text and paste it to this forum?

What i did see is that you are the only mortal user on this machine (davidd (uid=1000)).  The home directory exists and you have read and write permission to that directory.  There is no reason that you can't create a directory in your home directory.

Try this simple command from the terminal command line```
mkdir /home/davidd/test
```...if you get an error post that text here (no jpg's).

If you get no error, post the text output of these commands  (again -- no jpg's)```
pwd

ls -l /home/davidd
```

---

### Post by david472 on 2016-04-08
The reason I am posting jpg is that the server is a completely separate computer from the one I am using for the internet, hence taking a pic.  It is, in fact the computers are across the room from each other - and I have no laptop!  The server is a command line only machine, so I am not sure how copying and pasting would work or help.

```
mkdir /home/davidd/test
```

Says "error : /home/davidd/test : file exists"

---

### Post by bab1 on 2016-04-08
> **david472 said:**
> The reason I am posting jpg is that the server is a completely separate computer from the one I am using for the internet, hence taking a pic.  It is, in fact the computers are across the room from each other - and I have no laptop!  The server is a command line only machine, so I am not sure how copying and pasting would work or help.

This is how you learn. ;-)  Is the "other" computer a Ubuntu or Windows host?  In any event you can install Open-SSH s on your server.  Then you can remotely log in from the Ubuntu or Windows client.  If you are using Windows then you need to install PuTTY to be able to login to the server.
> 

```
mkdir /home/davidd/test
```

Says "error : /home/davidd/test : file exists"
So we do have a directory below /home/davidd.  Confirm that the test directory exist with this command```
ls -l /home/davidd
```...as you can see this is one of the commands that I asked for at the bottom.  The other command (pwd) tells you what is the working directory you are in.

---

### Post by mcgess on 2016-04-08
Hi

Just a suggestion but would it be a good idea to install samba onto the computer connected to the internet (assuming you have Ubuntu installed on that computer) and then when you have it working you'll have a better idea what to do to get samba working on the server the other side of the room. Doing this means you will be able to cut and paste commands and error/success messages onto the forum.

Going back a few posts you had an error message
```
cp missing destination file operand after  /etc/samba/smb.conf~
```
This looks like you missed a space before the ~ in the command
```
sudo cp /etc/samba/smb.conf ~
```

Martin

---

### Post by david472 on 2016-04-08
Ok, part of the issue is that I am restricted and cannot install any software on the WINDOWS computer I am working with here (other side of the room), but that is because the network erases anything after each boot.  I don't think that will be a problem as I will just reinstall it each time I use the computer.

I download the pttty.exe file (I think it is the newest one).  
It is asking me for the Host name to connect to the computer.  How do I figure that out?

As for the missing " ~" I will look into that.

---

### Post by mcgess on 2016-04-08
You can get the ip address of the server with the command (run on the server)
```
ifconfig -a
```
and looking for the **inet addr** in the eth section if you're hard cabled or wlan section if using a wireless connection

---

### Post by bab1 on 2016-04-08
> **mcgess said:**
> ...

Going back a few posts you had an error message
```
cp missing destination file operand after  /etc/samba/smb.conf~
```
This looks like you missed a space before the ~ in the command
```
sudo cp /etc/samba/smb.conf ~
```

Martin
This may not be what the OP was after.  It will create a file named "~"  I'd think this would be more appropriate ```
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.orig
or
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf~
```... as I said before; cp source to destination.

---

### Post by bab1 on 2016-04-08
> **david472 said:**
> Ok, part of the issue is that I am restricted and cannot install any software on the WINDOWS computer I am working with here (other side of the room), but that is because the network erases anything after each boot.  I don't think that will be a problem as I will just reinstall it each time I use the computer.

I download the pttty.exe file (I think it is the newest one).  
It is asking me for the Host name to connect to the computer.  How do I figure that out?

As @ mcgess has said, you don't need the hostname.  You can are better off using the IP address of the server.  If you want to know what the hostname is, look at the terminal prompt.  It shows the hostname after the @ symbol.  The syntax is **user@hostname**. 


You will need to install the SSH server on the Ubuntu host.  To do that you use these commands in this order```
sudo apt-get update

sudo apt-get install ssh 
```

---

### Post by mcgess on 2016-04-08
> **bab1 said:**
> This may not be what the OP was after.  It will create a file named "~"  I'd think this would be more appropriate ```
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.orig
or
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf~
```... as I said before; cp source to destination.

Or it might just create a copy of the file in the users home directory

---

### Post by bab1 on 2016-04-08
> **mcgess said:**
> Or it might just create a copy of the file in the users home directory
It will just confuse the issue to have a backup of the smb.conf file in the users home dir.  Better practice is to have the backup in the same dir as the working conf file (i.e. /etc/samba).  Yes?

---

### Post by mcgess on 2016-04-08
> If you want to know what the hostname is, look at the terminal prompt.   It shows the hostname after the @ symbol.  The syntax is **user@hostname**.

Talking of hostnames, I had trouble getting my samba server working because the hostname was too long. A none-google search (other search engines are available) led me to an article which stated that hostname should be 15 characters or less, samba apparently truncates it and can cause problems. Changing the hostname solved my problem

Martin

---

### Post by mcgess on 2016-04-08
> **bab1 said:**
> It will just confuse the issue to have a backup of the smb.conf file in the users home dir.  Better practice is to have the backup in the same dir as the working conf file (i.e. /etc/samba).  Yes?

Yes, I agree, that's how I'd do it. But the op was following instructions on a 'howto' and probably made a typo

---

### Post by bab1 on 2016-04-08
> **mcgess said:**
> Yes, I agree, that's how I'd do it. But the op was following instructions on a 'howto' and probably made a typo
Maybe.  If that is so, I'm not going to perpetuate the howto's poor advice.  ;-)

---

### Post by david472 on 2016-04-11
There was a lot of back and forth information since friday, so I hope I didn't miss anything.  I started with the update first.

Ok I started with  the install 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
sudo apt-get install ssh
```
That has downloaded and completed. 

Now I am trying to find the IP address.  I ran the command
```
 ifconfig -a
```
and I tried 
```
 ip addr show
```

Among all of the information, I am unclear what the IP address is? There is nothing that states IP address, like it would if I was using the GUI ([link]("http://www.howtogeek.com/howto/17012/how-to-find-your-ip-address-in-ubuntu/"))
There is something that says INET 10.xx.x.xxx etc.  So I am trying in Putty.

I tried the HOST NAME (@commtechserver without the @). This seems to work.  Now I am using the host shell to control the server, I believe.  What would be my next step?

---

### Post by bab1 on 2016-04-11
> **david472 said:**
> There was a lot of back and forth information since friday, so I hope I didn't miss anything.  I started with the update first.

Ok I started with  the install 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
sudo apt-get install ssh
```
That has downloaded and completed. 

Now I am trying to find the IP address.  I ran the command
```
 ifconfig -a
```
and I tried 
```
 ip addr show
```

Among all of the information, I am unclear what the IP address is? There is nothing that states IP address, like it would if I was using the GUI ([link]("http://www.howtogeek.com/howto/17012/how-to-find-your-ip-address-in-ubuntu/"))
There is something that says INET 10.xx.x.xxx etc.  So I am trying in Putty.

I tried the HOST NAME (@commtechserver without the @). This seems to work.  Now I am using the host shell to control the server, I believe.  What would be my next step?
The login shell of the host *commtechserver*, yes?.  Is that the remote Ubuntu host.  The local host should be the Windows host.  In this context the server is the Samba daemon (smbd) that is running on the host  *commtechserver*.

I think we should start at the beginning.  Post the output of these commands from the remote login terminal prompt```
pwd

ls -l /home

ls -ls -l /home/davidd

ls -l /etc/samba
```

You should be able to cut and paste all this info in the [noparse]```

```[/noparse] blocks by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the editor.

This is just the basic stuff, but from here we can do whatever you need.  Is this a testing environment for you to learn how this all works?

---

### Post by david472 on 2016-04-12
Ok I performed all of the functions using the remote server

```

davidd@commtechserver:~$ [COLOR=#ff0000]**pwd**[/COLOR]
/home/davidd
davidd@commtechserver:~$[COLOR=#ff0000]** ls -l /home**[/COLOR]
total 4
drwxr-xr-x 4 davidd davidd 4096 Apr  6 13:55 davidd
davidd@commtechserver:~$ [COLOR=#ff0000]**ls -ls -l /home/davidd**[/COLOR]
total 4
4 drwxrwxr-x 2 davidd davidd 4096 Apr  6 13:55 test
davidd@commtechserver:~$**[COLOR=#ff0000] ls -l /etc/samba[/COLOR]**
total 20
-rw-r--r-- 1 root root    0 Apr 12 14:43 dhcp.conf
-rw-r--r-- 1 root root    8 Mar  3 13:07 gdbcommands
-rw-r--r-- 1 root root 9542 Apr  4 15:59 smb.conf
drwxr-xr-x 2 root root 4096 Mar  3 13:06 tls
davidd@commtechserver:~$

```

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> Ok I performed all of the functions using the remote server

```

davidd@commtechserver:~$ [COLOR=#ff0000]**pwd**[/COLOR]
/home/davidd
davidd@commtechserver:~$[COLOR=#ff0000]** ls -l /home**[/COLOR]
total 4
drwxr-xr-x 4 davidd davidd 4096 Apr  6 13:55 davidd
davidd@commtechserver:~$ [COLOR=#ff0000]**ls -ls -l /home/davidd**[/COLOR]
total 4
4 drwxrwxr-x 2 davidd davidd 4096 Apr  6 13:55 test
davidd@commtechserver:~$**[COLOR=#ff0000] ls -l /etc/samba[/COLOR]**
total 20
-rw-r--r-- 1 root root    0 Apr 12 14:43 dhcp.conf
-rw-r--r-- 1 root root    8 Mar  3 13:07 gdbcommands
-rw-r--r-- 1 root root 9542 Apr  4 15:59 smb.conf
drwxr-xr-x 2 root root 4096 Mar  3 13:06 tls
davidd@commtechserver:~$

```
Let's take a look at what the smb.conf file looks like now.  Post the output of this command (you may have to scroll back to get it all)```
cat /etc/samba/smb.conf
```

Also post the output of this command```
cat /etc/samba/dhcp.conf
```...I don't there is anything in the file so don't worry if it comes up empty.

[COLOR="#0000FF"]**Edit: **Let's see if the Samba server is running at this point.  Post the output of this command[/COLOR]```
pgrep -l mbd
```...it should look something like this```
pgrep -l mbd
822 smbd
830 smbd
1967 nmbd

```

---

### Post by david472 on 2016-04-13
Ok, here is the first part, it is long, using this 
```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/samba/smb.conf[/FONT][/COLOR]
```


```
* Documentation:  https://help.ubuntu.com/Last login: Wed Apr 13 08:43:51 2016 from grs108707i.dsbnac.edu.on.ca
davidd@commtechserver:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller".
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de>                                                                                                                       for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\                                                                                                                      n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d                                                                                                                       /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

```

Now for the rest of what you asked
```
davidd@commtechserver:~$ cat /etc/samba/dhcp.conf
davidd@commtechserver:~$ pgrep -l mbd
594 smbd
653 smbd
798 nmbd
davidd@commtechserver:~$
```

---

### Post by bab1 on 2016-04-13
Great.  We have a clean smb.conf file and a running Samba server.

Let's make a copy of the smb.file as a backup to out edited file.  The command to do this is ```

sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.original
```...test your work and post the output with this```
ls -l /etc/samba
```...you should see the backup smb.conf file.

At this point we will use your user name for share access.  Later on we can use others.  In anticipation of having other users I suggest that we NOT use your user home directory to store shared data in.  We can make a directory that all users will be able to access.  I'm not going to worry about the partition size at this point as this is just a test share we are making.

To create the directory we use this command```
sudo mkdir -p /data/test
```...this will create the the directory */data *and the subdirectory of */data/test*.  Post the output of this command to see the work```
ls -l /data
```

For the first part of the test we will make your user the owner of the test directory with this command```
sudo chown davidd:davidd /data/test
```...post the output of this command (again)```
ls -l /data
```...see the difference?

Now try and create a file in that directory with this command (NO sudo on this one)```
touch /data/test/file1 file2 
```..Lets show the files with this command```
ls -l /data/test
```

If you are successful, you should have been able to make 2 files in the directory /data/test .

---

### Post by david472 on 2016-04-13
Here is the output from what you asked.

```

davidd@commtechserver:~$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original                                                                                                                      l
davidd@commtechserver:~$ ls -l /etc/samba
total 32
-rw-r--r-- 1 root root    0 Apr 13 08:17 dhcp.conf
-rw-r--r-- 1 root root    8 Mar  3 13:07 gdbcommands
-rw-r--r-- 1 root root 9542 Apr  4 15:59 smb.conf
-rw-r--r-- 1 root root 9542 Apr 13 12:32 smb.conf.original
drwxr-xr-x 2 root root 4096 Mar  3 13:06 tls
davidd@commtechserver:~$ sudo mkdir -p /data/test
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root   16384 Mar 15 13:32 lost+found
drwxr-xr-x 2 davidd davidd  4096 Apr 13 12:29 test
davidd@commtechserver:~$ sudo chown davidd:davidd /data/test
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root   16384 Mar 15 13:32 lost+found
drwxr-xr-x 2 davidd davidd  4096 Apr 13 12:29 test
davidd@commtechserver:~$ touch /data/test/file1 file2
davidd@commtechserver:~$ ls -l /data/test
total 0
-rw-rw-r-- 1 davidd davidd 0 Apr 13 12:33 file1
davidd@commtechserver:~$

```

---

### Post by bab1 on 2016-04-13
It all looks good.

Post back the output of this command```
df -ah
```

---

### Post by david472 on 2016-04-13
Ok, thanks for the quick response: 

```
davidd@commtechserver:~$ df -ahFilesystem                           Size  Used Avail Use% Mounted on
sysfs                                   0     0     0    - /sys
proc                                    0     0     0    - /proc
udev                                 976M   12K  976M   1% /dev
devpts                                  0     0     0    - /dev/pts
tmpfs                                198M  828K  197M   1% /run
/dev/mapper/commtechserver--vg-root  228G  1.2G  216G   1% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
none                                    0     0     0    - /sys/fs/fuse/connections
none                                    0     0     0    - /sys/kernel/debug
none                                    0     0     0    - /sys/kernel/security
none                                 5.0M     0  5.0M   0% /run/lock
none                                 986M     0  986M   0% /run/shm
none                                 100M     0  100M   0% /run/user
none                                    0     0     0    - /sys/fs/pstore
/dev/md0                             917G   72M  870G   1% /data
/dev/sdb1                            236M   37M  187M  17% /boot
systemd                                 0     0     0    - /sys/fs/cgroup/systemd

```

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> Ok, thanks for the quick response: 

```
davidd@commtechserver:~$ df -ahFilesystem                           Size  Used Avail Use% Mounted on
sysfs                                   0     0     0    - /sys
proc                                    0     0     0    - /proc
udev                                 976M   12K  976M   1% /dev
devpts                                  0     0     0    - /dev/pts
tmpfs                                198M  828K  197M   1% /run
/dev/mapper/commtechserver--vg-root  228G  1.2G  216G   1% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
none                                    0     0     0    - /sys/fs/fuse/connections
none                                    0     0     0    - /sys/kernel/debug
none                                    0     0     0    - /sys/kernel/security
none                                 5.0M     0  5.0M   0% /run/lock
none                                 986M     0  986M   0% /run/shm
none                                 100M     0  100M   0% /run/user
none                                    0     0     0    - /sys/fs/pstore
/dev/md0                             917G   72M  870G   1% /data
/dev/sdb1                            236M   37M  187M  17% /boot
systemd                                 0     0     0    - /sys/fs/cgroup/systemd

```
Did you know to mount the RAID array at /data?

---

### Post by david472 on 2016-04-13
No I don't know how.  I thought the RAID system was done, but I am clueless as you can tell.

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> No I don't know how.  I thought the RAID system was done, but I am clueless as you can tell.
Interesting as **df -ah** clearly shows the raid array mounted specifically at /data.  See```
/dev/md0                             917G   72M  870G   1% /data
```  I guess it was configured previously for /data and I just lucked out that this was where the data was going to go.  Normally I put my shared files at /srv. But this works just as well.

Let's create a Samba share at /data/test.  You will have to edit the smb.conf file by adding some text at the bottom.  Open the file with this command ```
sudo nano /etc/samba/smb.conf
```

Then add this to the very bottom of that file> 
[Test_Share]
        comment = Test Data
        path = /data/test
        browseable = yes
        guest ok = yes
        writeable = yes
        create mask = 0664
        force directory mode = 0775
...Exit the editor and save the file.

You have to restart the Samba file sharing daemon (smbd).  To do that you use this command```
sudo seervice smbd restart
```
After a few minutes you should be able to see the share when you open the file browser and click on "Browse Network".  Click on the share.  Uuse your username and login and see if it opens.  Can you edit the files or create new ones?

---

### Post by david472 on 2016-04-13
I edited the file, saved it and exit.


Then I tried to restart : ( I corrected the seervice part)
```
 davidd@commtechserver:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 1840

```


Ok, the network shows the commtechserver.  I can go to the folder called test_share.  When I try to place files in it, it tells me "you need permission to perform this function"

So I would like to get a batch file command line from windows to open up the server.  How can I go about this?  Also, I need a password so that only certain people are able to access via a batch file or otherwise.  Any suggestions?

---

### Post by david472 on 2016-04-13
The old server had this command for the the windows machine :

[COLOR=#000000][FONT=HelveticaNeue]```
net use z: \\commtechserver\video /user:vidshare vidshare
```

[FONT=arial]I don't have any users but myself, so I am guessing I need to create this user (and if you tell me how please)[/FONT]


[/FONT][/COLOR]

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> I edited the file, saved it and exit.


Then I tried to restart : ( I corrected the seervice part)
```
 davidd@commtechserver:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 1840

```


Ok, the network shows the commtechserver.  I can go to the folder called test_share.  When I try to place files in it, it tells me "you need permission to perform this function"

So I would like to get a batch file command line from windows to open up the server.  How can I go about this?  Also, I need a password so that only certain people are able to access via a batch file or otherwise.  Any suggestions?

> I don't have any users but myself, so I am guessing I need to create this user (and if you tell me how please)

Slowdown.  We will get to where you want to be.  I'll help all the way.  To set the permissions on the folder you need use this command```
sudo chmod 775 /data/test
```...post the output of this ```
ls -l /data
```

Try adding a file to the share now.  If successful post the output of this```
ls -l /data/test
```

You should be using the Windows machine for browsing the share and the Putty command line to directly access the server.

---

### Post by david472 on 2016-04-13
It did NOT allow me to share even after the chmod code.  I am running all of this from Putty.

Here is the output of 
```
ls -l /data

davidd@commtechserver:~$ sudo chmod 775 /data/test
[sudo] password for davidd:
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root   16384 Mar 15 13:32 lost+found
drwxrwxr-x 2 davidd davidd  4096 Apr 13 12:29 test

```

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> It did NOT allow me to share even after the chmod code.  I am running all of this from Putty.

Here is the output of 
```
ls -l /data

davidd@commtechserver:~$ sudo chmod 775 /data/test
[sudo] password for davidd:
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root   16384 Mar 15 13:32 lost+found
drwxrwxr-x 2 davidd davidd  4096 Apr 13 12:29 test

```What user are you logging into the share as?

What are the owership/permissions on the path to the share?  We can see that with these commands
```
ls -l /

ls -l /data/test
```

---

### Post by david472 on 2016-04-13
I am logged into the Windows network using my work login and password. Everything I have been doing is in windows (putty).  I am dragging and dropping/copying files using windows as well.  Logging into the the server is completely different.  On the server (and through putty), I use **davidd** login and **password**.
  In windows, I am not sure how to login to the server (davidd) to do the file copying.  I thought that the batch file might log me in, but I am wrong most of the time, so what do I know?

Here is the output:
```


davidd@commtechserver:~$ ls -l /
total 81
drwxr-xr-x   2 root root  4096 Mar 11 14:25 bin
drwxr-xr-x   4 root root  1024 Mar 15 16:49 boot
drwxr-xr-x   4 root root  4096 Apr 13 12:24 data
drwxr-xr-x  17 root root  4540 Apr 13 08:16 dev
drwxr-xr-x  87 root root  4096 Apr 13 12:21 etc
drwxr-xr-x   3 root root  4096 Mar 11 14:43 home
lrwxrwxrwx   1 root root    32 Mar 11 13:52 initrd.img -> boot/initrd.img-4.2.0-30-generic
drwxr-xr-x  22 root root  4096 Mar 11 14:25 lib
drwx------   2 root root 16384 Mar 11 13:42 lost+found
drwxr-xr-x   2 root root  4096 Mar 11 13:42 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   2 root root  4096 Mar 11 13:44 opt
dr-xr-xr-x 113 root root     0 Apr 13 08:16 proc
drwx------   2 root root  4096 Mar 15 18:44 root
drwxr-xr-x  19 root root   600 Apr 13 15:18 run
drwxr-xr-x   2 root root 12288 Mar 12 15:27 sbin
drwxr-xr-x   2 root root  4096 Mar 11 13:44 srv
dr-xr-xr-x  13 root root     0 Apr 13 08:16 sys
drwxrwxrwt   2 root root  4096 Apr 13 15:17 tmp
drwxr-xr-x  10 root root  4096 Mar 11 13:44 usr
drwxr-xr-x  11 root root  4096 Mar 11 13:44 var
lrwxrwxrwx   1 root root    29 Mar 11 13:52 vmlinuz -> boot/vmlinuz-4.2.0-30-generic
davidd@commtechserver:~$ ls -l /data/test
total 0
-rw-rw-r-- 1 davidd davidd 0 Apr 13 12:33 file1
davidd@commtechserver:~$
```

---

### Post by bab1 on 2016-04-13
> **david472 said:**
> I am logged into the Windows network using my work login and password.  
My guess is that the Windows user/pass is not the same as on the Ubuntu host.  Is that correct?  Lets change a few things to the share definition.  See my comments below
> 
The server is completely different, this using the davidd login and password.  In windows, I am not sure how to login to the server to do the file copying.

There are 2 methods of manipulating files and directories (folders).  The first way is loging in to the local host (commtechserver).  This is the direct way.  The second way is to log into the Samba (Windows) share.  This is the remote way.  

Which method you use will dictate what you are doing.  SSH (via Putty) is considered local administration, while logging into a file share is always remote access for the users. 
>   
I thought that the batch file might log me in, but I am wrong most of the time, so what do I know?

Most likely so... ;-)  That's why I'm trying to show you how its done rather than just telling you "do this".

Let's modify the share to this```

[Test_Share]
comment = Test Data
path = /data/test
browseable = yes
[COLOR="#FF0000"]guest ok = no  <<-- This is changed
valid users = davidd  << -- This is changed[/COLOR]
writeable = yes
create mask = 0664
force directory mode = 0775 
```
Change the parameters to those indicated in red.  Restart the Samba server with this ```
sudo service smbd restart
```... wait a few minutes and see if you can log in using the user/pass of *davidd* and create or edit files and directories.

---

### Post by david472 on 2016-04-14
success!  excellent.,that works. I changed the config file where you asked and it does indeed now prompt me for davidd and the password.  I copied a file and it runs from the server.

1) So is the next step adding a BLANK user or Guest user?
2) I still don't know enough about how to change the config file to ADD a user.
3) I am guessing you know enough about windows to help with a batchfile (when the time comes)...

---

### Post by bab1 on 2016-04-14
> **david472 said:**
> success!  excellent.,that works. I changed the config file where you asked and it does indeed now prompt me for davidd and the password.  I copied a file and it runs from the server.

1) So is the next step adding a BLANK user or Guest user?
2) I still don't know enough about how to change the config file to ADD a user.
3) I am guessing you know enough about windows to help with a batchfile (when the time comes)...
Great.  Now that the basic file share is working I need to know what user(s) that are going to to have access.  By this I mean Linux/Samba users not humans that are using the computer.  Do you want individual user accounts or one user account for all humans to use?  In my network each person has a separate user account that is also a Samba user account.  I havae shares that are configured so multiple users have access to so the same data.

You do not add users with the config file.  That is a separate command.  You can configure a share parameter to accept "group" user access.  The group is created outside of the smb.conf file.  I need to know how you envision the group if we are using that style of file sharing.

What batch file?  What do you want to accomplish with it?  

It's easier if you state your end goal(s).  Then I will know how we should configure the services.  I need more than "I am using it as a video server so that people can put their video files on it and edit them from a windows machine."   If we have one Samba account there is no security.  Any user can delete the data.  If you have separate accounts then the individual users can't see the other persons data.  Somewhere in between is multiple shares that are restricted by group membership.

[COLOR="#0000FF"]Edit:  This is for data storage.  I hope you are not going to try video editing via remote file stores.[/COLOR]

---

### Post by david472 on 2016-04-14
To answer your questions :

1) They are going to be Window's users that are going to storing video files on the server. 

2) I need multiple, single logins for each users of the storage space. AND I want  to enable multiple users that can access the same storage at the same time if needs be from a window(s) computer. 

3) Multiple user accounts (beside my davidd account - admin).  I want multiple users to have access to the same storage and data.  They will log them in under vidshare 1, vidshare 2, vidshare 3 etc. with their own passwords (which they will have to give me)

4) The batch file was something that the user clicked on in windows and it automatically brought up the login prompt for their password and login.  They didn't need to look into window explorer to find the commtechserver.

I hope this is clear.

---

### Post by bab1 on 2016-04-14
> **david472 said:**
> To answer your questions :

1) They are going to be Window's users that are going to storing video files on the server. 

2) I need multiple, single logins for each users of the storage space. AND I want  to enable multiple users that can access the same storage at the same time if needs be from a window(s) computer. 

3) Multiple user accounts (beside my davidd account - admin).  I want multiple users to have access to the same storage and data.  They will log them in under vidshare 1, vidshare 2, vidshare 3 etc. with their own passwords (which they will have to give me)

4) The batch file was something that the user clicked on in windows and it automatically brought up the login prompt for their password and login.  They didn't need to look into window explorer to find the commtechserver.

I hope this is clear.
1. Storing the video files works.  Most likely the Windows client can stream them too (within reasonable restraints).

2. This can be done.  How ever you configure the share for multiple user access, not the user accounts.  You can have a mix of private shares (single user access) and semi private (user-group) access and public (all users access).
 
3. The user accounts most likley should be in the users name (e.g. johnj or jjones or  bills or bsmith etc.)  The  groups can be any name name you want (e.g. vid1, vid2 etc.)  The username is seen by the users every time they log in.  The group name is never seen.  The group name helps the admin view the log files if there is a problem. 

4.  You log in to a Samba share (the SMB resource), not to Samba generally.  Browsing allows you to see all the shares.  If you have multiple shares for different groups you will have  multiple SMB resources.  This is what Windows calls "mapping drives.  I have no recent (less than 20 years ago) Windows administrator experience so I'm not going to be much help in that way.

How many users are there?  Do you want private shares for each of them?  How many different user groups do you need?  We will need to create the data structure for all the shares (e.g /data/home,  /data/vid1, /data/vid2, etc.)  Then we can add the users.

When adding the Linux user you can add a home directory.  This can be the "private share" I have mentioned.  This share is configured only once and it expands the [homes] share for each user.  One share <--> Multiple private shares.  We get to define where that home dir resides.  I think /data/home is a perfect place for this if we are using private data shares.

So these are the design considerations needed; usernames, home dir or not, how many user-groups, directory structure of the data stores.

---

### Post by david472 on 2016-04-14
I'll go throug has much as I understand right now

1) Storing ok
2) I think I need single user access for now
3) Do I need groups?  Cannot I not just give them single user accounts?  There is only going to be three users as of now
4) Ok, I will try and figure out how to batch file it.  Thanks anyway.

-Three users - for now user1, user2, user3 until I get them sorted on monday.
-Private shares (does thing mean their own login? Will they be able to access the same files at the same time if necessary with private?)
-Only one group - Vidshare1

I think I answered everything.

---

### Post by bab1 on 2016-04-14
> **david472 said:**
> I'll go through has much as I understand right now

1) Storing ok
2) I think I need single user access for now
3) Do I need groups?  Cannot I not just give them single user accounts?  There is only going to be three users as of now
4) Ok, I will try and figure out how to batch file it.  Thanks anyway.

-Three users - for now user1, user2, user3 until I get them sorted on monday.
-Private shares (does thing mean their own login? Will they be able to access the same files at the same time if necessary with private?)
-Only one group - Vidshare1

I think I answered everything.
It's easy to have multiple users access the same directory and files.  The ownership of those objects are by 3 owner groups.  These are: [COLOR="#0000FF"]owner[/COLOR]:[COLOR="#FF0000"]group[/COLOR]:[COLOR="#008000"]others[/COLOR].  An example of that is this```
ls -l /data
total 20
d[COLOR="#0000FF"]rwx[/COLOR]------ 2 [COLOR="#0000FF"]root[/COLOR]   [COLOR="#FF0000"]root[/COLOR]   16384 Mar 15 13:32 lost+found
d[COLOR="#0000FF"]rwx[/COLOR][COLOR="#FF0000"]rwx[/COLOR][COLOR="#008000"]r-x[/COLOR] 2 [COLOR="#0000FF"]davidd[/COLOR] [COLOR="#FF0000"]davidd[/COLOR]  4096 Apr 13 12:29 test
```...In this you can see the group ownership and permissions in red.  By creating a directory where the group owner is a a user-group that all the user are in, then all the users will have access.

All users (bill, bob and john) will can be part of the group vidshare1.  So the ownership is like this <user>:vidshare1:others.  The permissions are rwx:rwx:r-x.  The [COLOR="#0000FF"]user[/COLOR] can read, write and eXecute :: the [COLOR="#FF0000"]group[/COLOR] can read, write an eXecute :: the [COLOR="#008000"]others[/COLOR] (everyone) can read and eXecute.  In other words it is a 2 step security process; ownership and permissions.

It is important to understand that there are 2 types of logins.  They are the Linux login (interactive) and the Samba login (to the share).  The remote Samba user never logs into the system.

Here is all you need to do to create a user with no interactive login (this is called a system user)```

sudo adduser --system --no-create-home <user_name>
``` ...where <user_name> the name of the user.  This user can't login to Ubuntu and has no home directory (/home/).

Then you can add the user to the Samba user database with this command```
sudo smbpasswd -a <user_name>
```...enter the password that you want the user to have (remember this password.  It is for the user access to the Samba shares.

Now you have to create the user group, such as *vidshare1*, and add all the users to it.  Even if you only create one vid user you will need to do this so you can add davidd and the single vid user.  That way you and the vid users will both be able to access the data.  To create the group use this command```
sudo addgroup --system <group_name>
```...where <group_name> is your choice of name

Now you add the user to the group ```
sudo adduser <user_name>  <user_group>
```...an example would be "*sudo adduser john vidgroup*".

Now we can check the work with these commands```
tail -n5 /etc/password

tail -n5 /etc/group

sudo pdbedit -L
```...post the output of all of these.

If you have **any** questions please ask **before** you use the commands.

---

### Post by david472 on 2016-04-14
I see where you are going with this.  Creating a user, and then creating a place for the user to reside.  It seems that the user1 is going to reside in Vidshare, but davidd does not.

Here is the output of the code :```

davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root   16384 Mar 15 13:32 lost+found
drwxrwxr-x 2 davidd davidd  4096 Apr 14 12:53 test
davidd@commtechserver:~$ sudo adduser --system --no-create-home user1
[sudo] password for davidd:
Adding system user `user1' (UID 105) ...
Adding new user `user1' (UID 105) with group `nogroup' ...
Not creating home directory `/home/user1'.
davidd@commtechserver:~$ sudo smbpasswd -a user1
New SMB password:
Retype new SMB password:
Added user user1.
davidd@commtechserver:~$ sudo addgroup --system vidshare
Adding group `vidshare' (GID 114) ...
Done.
davidd@commtechserver:~$ sudo adduser user1 vidshare
Adding user `user1' to group `vidshare' ...
Adding user user1 to group vidshare
Done.
davidd@commtechserver:~$ tail -n5 /etc/passwd
messagebus:x:102:105::/var/run/dbus:/bin/false
davidd:x:1000:1000:davidd,,,:/home/davidd:/bin/bash
postfix:x:103:112::/var/spool/postfix:/bin/false
sshd:x:104:65534::/var/run/sshd:/usr/sbin/nologin
user1:x:105:65534::/home/user1:/bin/false
davidd@commtechserver:~$ tail -n5 /etc/group
sambashare:x:110:davidd
ssl-cert:x:111:
postfix:x:112:
postdrop:x:113:
vidshare:x:114:user1
davidd@commtechserver:~$ sudo pdbedit -L
davidd:1000:davidd
user1:105:
davidd@commtechserver:~$

```

1) Now, do I need to reboot the samba server for this to take effect? (did it)  The reason I ask is that I just tried to login using  login : user1  password : xxxx and it said authentication failed.
2) I am assuming the Vidshare will have a different folder than davidd?  Will they be able to access each other's? 
3) I am logged in using davidd mapping/network (windows) and I need to log out to test the other user1, do you know how to do that?  Do I need to reboot windows?

---

### Post by bab1 on 2016-04-14
> **david472 said:**
> I see where you are going with this.  Creating a user, and then creating a place for the user to reside.  It seems that the user1 is going to reside in Vidshare, but davidd does not.

Sort of but not really.  The user group is for access control.  Both ddavid and user1 belong in the user group vidshare. 
> 
Here is the output of the code :```

davidd@commtechserver:~$ tail -n5 /etc/passwd
davidd:x:1000:1000:davidd,,,:/home/davidd:/bin/bash
user1:x:105:65534::/home/user1:/bin/false

davidd@commtechserver:~$ tail -n5 /etc/group
vidshare:x:114:user1  [COLOR="#FF0000"]**<<-- need to add davidd to this group**[/COLOR]

davidd@commtechserver:~$ sudo pdbedit -L
davidd:1000:davidd
user1:105:

```
You need to add the user *davidd* to the *vidshare* group with this command```
sudo adduser davidd vidshare
```...then the users *davidd* and *user1* have a common group membership so that the can both have access to data where the group owner is vidshare.
> 
1) Now, do I need to reboot the samba server for this to take effect? (did it)  The reason I ask is that I just tried to login using  login : user1  password : xxxx and it said authentication failed.

Login to what?  There is no login using PuTTY (no interactive login), nor is there a Samba share that will give user1 access.
> 
2) I am assuming the Vidshare will have a different folder than davidd?  Will they be able to access each other's?

That's what I've been trying to tell you.  You can make Samba shares that only *user1* or *davidd* can access or the share can be configured so that all users that are members of the user-group *vidshare* will have access to a Samba share.  Follow along and you shall see.  ;-)
>  
3) I am logged in using davidd mapping/network (windows) and I need to log out to test the other user1, do you know how to do that?  Do I need to reboot windows?
Accessing the share is what you call it.  We need to configure a share for user1 to access before you can test it.  First add *davidd* to the *vidshare* group and post the output again of  ```
tail -n5 /etc/group
```

---

### Post by david472 on 2016-04-15
ok I added davidd to vidshare. Here is the output :

```
davidd@commtechserver:~$ sudo adduser davidd vidshare[sudo] password for davidd:
Adding user `davidd' to group `vidshare' ...
Adding user davidd to group vidshare
Done.
davidd@commtechserver:~$ tail -n5 /etc/group
sambashare:x:110:davidd
ssl-cert:x:111:
postfix:x:112:
postdrop:x:113:
vidshare:x:114:user1,davidd

```

I can see that user1 and davidd are in the vidshare folder.

> [COLOR=#000000]Login to what? There is no login using PuTTY (no interactive login), nor is there a Samba share that will give user1 access.[/COLOR]

When I am in windows and see the network - it has the commtechserver listed.  I can then click on it and see what is inside the folder (test_share) BUT first there is a login screen to get into the folder (test_share).  That is what I was referring to, but maybe I was getting a head of myself.  The login I am speaking of works for davidd, but not for user1 yet.

Again if I haven't said thank you yet, I am sorry.  I do appreciate all the help!

---

### Post by bab1 on 2016-04-15
> **david472 said:**
> ok I added davidd to vidshare. Here is the output :

```
davidd@commtechserver:~$ sudo adduser davidd vidshare[sudo] password for davidd:
Adding user `davidd' to group `vidshare' ...
Adding user davidd to group vidshare
Done.
davidd@commtechserver:~$ tail -n5 /etc/group
sambashare:x:110:davidd
ssl-cert:x:111:
postfix:x:112:
postdrop:x:113:
vidshare:x:114:user1,davidd

```

I can see that user1 and davidd are in the vidshare folder.

The listings you see are in a simple text file.  The vidshare group is not a folder.  It's just a listing of the group name, gid and users that are members of that group.
> 
When I am in windows and see the network - it has the commtechserver listed.  I can then click on it and see what is inside the folder (test_share) BUT first there is a login screen to get into the folder (test_share).  That is what I was referring to, but maybe I was getting a head of myself.  The login I am speaking of works for davidd, but not for user1 yet.
Yes.  The Samba share login.

Let's make the test share available for the user named user1.  We have to change the user-group ownership of the directory to vidshare.  We do that with this command```
sudo chgrp vidshare /data/test
```
I also set the SGID bit to force the setting of the vidshare group on all files and directories that are created in this directory.  We do that with these commands in this order```
sudo chmod -R ug=rwX,o=rX /data/test

sudo chmod g+s /data/test
```...post the output of these commands so I can check the work```
ls -l /data

ls -l /data/test
```
Now we modify the share definition to this (see the red part)```

[Test_Share]
comment = Test Data
path = /data/test
browseable = yes
guest ok = no  
valid users = [COLOR="#FF0000"]+vidshare [/COLOR] << -- This is changed from davidd to +vidshare
[COLOR="#FF0000"]force group = vidshare [/COLOR]  <<-- this is added to ensure that the user-group is always vidshare
writeable = yes
create mask = 0664
force directory mode = 0775
```
To edit the file you use this command```
sudo nano /etc/samba/smb.conf
```...I want to see the file so post the output of this```
cat /etc/samba/smb.conf
```

Since we have modified the smb.conf file we need to restart the Samba server with this command```
sudo service smbd restart
```
At this point the either user in the vidshare user group can log in to the share and create files and directories.

---

### Post by david472 on 2016-04-15
Ok here is the output, working on the rest next
```
davidd@commtechserver:~$ sudo chgrp vidshare /data/test[sudo] 
password for davidd:
davidd@commtechserver:~$ sudo chmod -R ug=rwx,o=rX /data/test
davidd@commtechserver:~$ sudo chmod g+s /data/test
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root     16384 Mar 15 13:32 lost+found
drwxrwsr-x 2 davidd vidshare  4096 Apr 14 12:53 test
davidd@commtechserver:~$ ls -l /data test
/data:
total 20
drwx------ 2 root   root     16384 Mar 15 13:32 lost+found
drwxrwsr-x 2 davidd vidshare  4096 Apr 14 12:53 test


test:
total 0

```

Here is the change after adding vidshare+
```

Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 4.2.0-30-generic i686)


 * Documentation:  https://help.ubuntu.com/
Last login: Fri Apr 15 12:10:34 2016 from grs108707i.dsbnac.edu.on.ca
davidd@commtechserver:~$ cat /etc/samba/smb.conf


#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller".
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
# BAB1 info from ubuntu forums general samba server update
[Test_Share]
comment = Test Data
path = /data/test
browseable = yes
guest ok = no
valid users = +vidshare
force group = vidshare
writeable = yes
create mask = 0664
force director mode = 0775

```

I have also restarted the server, as you requested.

---

### Post by bab1 on 2016-04-15
> **david472 said:**
> Ok here is the output, working on the rest next
```
davidd@commtechserver:~$ sudo chgrp vidshare /data/test[sudo] 
password for davidd:
davidd@commtechserver:~$ sudo chmod -R ug=rwx,o=rX /data/test
davidd@commtechserver:~$ sudo chmod g+s /data/test
davidd@commtechserver:~$ ls -l /data
total 20
drwx------ 2 root   root     16384 Mar 15 13:32 lost+found
drwxrwsr-x 2 davidd vidshare  4096 Apr 14 12:53 test
davidd@commtechserver:~$ ls -l /data test
/data:
total 20
drwx------ 2 root   root     16384 Mar 15 13:32 lost+found
drwxrwsr-x 2 davidd vidshare  4096 Apr 14 12:53 test


test:
total 0

```
Looks good so far.

---

### Post by bab1 on 2016-04-15
I see a typo in the share parameter.  The last line:
[FONT=Courier New]**force director mode = 0775**[/FONT]
should be:
[FONT=Courier New]**force director[B][COLOR="#FF0000"]y[/COLOR]** mode = 0775[/B][/FONT]

You need to restart the Samba server again.

---

### Post by david472 on 2016-04-15
[FONT=arial]Fixed.  Thank you.

Ok, I am assuming I create all new users this way, right?

1) Also, for as far as administrative privileges, is there a way I can dates, times, when the users are active?

Ok, to summarize - when adding a new user

1) Add user```
[COLOR=#000000]sudo adduser --system --no-create-home <user_name>[/COLOR]
```[COLOR=#000000]

2) Password for user [/COLOR]```
[COLOR=#000000]sudo smbpasswd -a <user_name>[/COLOR]
```[COLOR=#000000]

[/COLOR][COLOR=#000000]3) Add user to vidshare group[/COLOR]```
[COLOR=#000000]sudo adduser <user_name>  <user_group>[/COLOR]
```[COLOR=#000000]

[/COLOR][COLOR=#000000]4) Checking it after [/COLOR]```
[COLOR=#000000]tail -n5 /etc/password[/COLOR]
tail -n5 /etc/group

sudo pdbedit -L
```

5) Check users 
```
ls -l /data
ls -l /data/test
```

6) Restart server
```
sudo service smbd restart
```

[COLOR=#000000]Forgive me if I missed anything, there is a lot here.[/COLOR][/FONT]

---

### Post by bab1 on 2016-04-15
There is a lot there.  I was assuming that the /data/test directory was just that; a test.  The share is easy to rename and reset the path.

Is the share working?  Can both users have access?  What does the newly created file ownership and permissions look like?

---

### Post by bab1 on 2016-04-15
> **david472 said:**
> Fixed.  Thank you.

Ok, I am assuming I create all new users this way, right?

Yes.
> 

1) Also, for as far as administrative privileges, is there a way I can dates, times, when the users are active?

There are the logs at:  /var/log/samba
The general logs are at: /var/log
The real time monitor is: sudo smbstatus

The format for *smbstatus* looks like this```
Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

```...all text so the output can be used in a script.  I don't monitor my users at all.  If I have a problem I consult the logs.  That is why you want to use non-ambiguous user-names. 

All the steps you listed are correct for adding a user to Ubuntu and Samba.

---

### Post by david472 on 2016-04-15
thank you again.  I will start the users on Monday, so I don't want to close the thread as solved just yet if that is ok.

---

### Post by bab1 on 2016-04-15
> **david472 said:**
> thank you again.  I will start the users on Monday, so I don't want to close the thread as solved just yet if that is ok.
Are you going to leave the share as it is?  The data at /data/test and the share name as [Test]?

---

### Post by david472 on 2016-05-02
Ok, after playing with it for a little while - here is one of the issues :

I want to be the superuser, so to speak, that can look into all of the files that user1, user2 etc work on.  Right now, I cannot look at files, change folders etc from davidd.  Is there a way that I can be the admin and do this?

---

### Post by bab1 on 2016-05-02
> **david472 said:**
> Ok, after playing with it for a little while - here is one of the issues :

I want to be the superuser, so to speak, that can look into all of the files that user1, user2 etc work on.  Right now, I cannot look at files, change folders etc from davidd.  Is there a way that I can be the admin and do this?

Sure you can.  Just ssh to the host and use sudo at the Linux directory that is shared.  I would never admin a Samba file share directly.  

If you insist, you can make any Samba user the superuser for just that share by adding this parameter to the share definition```
admin user = <user-name>
```...where <user-name> is the Samba user you want to be an admin.  Warning: you can mess up the permissions and ownership of the share doing this.  This user should not be also a regular user of the share.

---

### Post by david472 on 2016-06-21
My server, today and only today, is no longer listed on the network.  This is strange.  I can access it remotely using putty, but can't access it using Windows.  Any ideas?

I did a samba status :
 smbstatus


```
Samba version 4.1.6-UbuntuPID     Username      Group         Machine
-------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files



```

---

### Post by bab1 on 2016-06-21
> **david472 said:**
> My server, today and only today, is no longer listed on the network.  This is strange.  I can access it remotely using putty, but can't access it using Windows.  Any ideas?

I did a samba status :
 smbstatus


```
Samba version 4.1.6-UbuntuPID     Username      Group         Machine
-------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files



```
This is not the same problem as the OP.   Start a new thread.  No PM's pls.

---

