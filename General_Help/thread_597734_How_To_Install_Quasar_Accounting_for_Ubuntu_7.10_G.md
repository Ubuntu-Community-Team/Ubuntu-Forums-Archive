---
title: "How To: Install Quasar Accounting for Ubuntu 7.10 Gutsy"
date: 2007-10-30
forum: General Help
---

### Post by Sabot on 2007-10-30
I have created a deb file that should make the process of installing Quasar a little less painful. It is for 32bit x86 systems only.  You can download the file from this address: [http://briefcase.yahoo.com/bc/sabot300@att.net/lst?&.dir=/Quasar&.src=bc&.view=l]("http://briefcase.yahoo.com/bc/sabot300@att.net/lst?&.dir=/Quasar&.src=bc&.view=l")
Once the file is downloaded, just double click and install. Once the package is installed it with say in the Status: Error Conflicts with the installed package 'quasar'.  This is normal and it just means you have installed the Quasar package.

Then enter Into a terminal window:
```
sudo su postgres
```
Now we need to create two accounts for the database Quasar uses.
```
createuser -d -E -P quasar-dba
```
```
createuser -E -P quasar
```
Enter a password of abc123 for both users. Answer Yes to all questions.
This package will not work if you use different users and passwords. You can change them later.

Next we need to create an account on your computer that has Quasar as it's home directory. Open another terminal window and enter:
```
sudo useradd quasar --home /opt/quasar
```
Restart your computer and you are ready to use Quasar. You will find two launchers for  Quasar under Applications>Office.
Use Quasar Admin to create a database. The default username and password for your database will be admin. Open Quasar and login into your database. A user guide can be found at [http://www.linuxcanada.com/](http://www.linuxcanada.com/).

---

### Post by sigma_solutions on 2007-11-28
hi there. what are the dependencies of your quasar deb package?

---

### Post by Sabot on 2007-11-28
The dependencies are:

libqt3-mt
tcl8.4
tk8.4
libpq5
postgresql-8.2
libicu36
xinetd

---

### Post by sigma_solutions on 2007-11-29
thanks got it working perfectly! you should submit the file to ubuntu for inclusion in their repositories. also you should add a note saying that the quasar admin shortcut needs to be changed for kubuntu users (we use sudo not gksudo) and it needs to start in the terminal. but other than that it works flawlessly

---

### Post by art.by.bec.com on 2007-12-08
Hi,
I am new to linux and just stuffed up

i was trying to get quasar
i found a blog here that suggested what to do
[https://help.ubuntu.com/community/QuasarAccountingInstallation](https://help.ubuntu.com/community/QuasarAccountingInstallation)
i got past downloading quasar and as far as 
gedit install     where i was supposed to alter the code
gedit opened but there wasnt any code there so i came to a halt

then i found this discussion
i downloaded the file (linked above) but it conflicts with the already install quasar
i tried to get rid of quasar.... you can tell i am completely new t this cant you!!!
not sure how to even do that and cant find the files either

i love linux but seriously do you need to be a brain surgeon????

I am opening my new small business next week and am terrified because i can't find a small business solution on linux
i have spent weeks reading blogs looking at programs (i came from quickbooks)
i have come to linux because the new computer system i purchased was vista (it wouldn't let me install any of my aged programs) and wanted me to purchace all the latest ms programs.. let alone all the web design, photo editing etc i use
i refuse to let ms beat me!!!
please help!


thanks bec

---

### Post by Sabot on 2007-12-08
Bec if you open up synaptic, it should allow you to seach for quasar and then remove it.  Then you can install my package and follow the instructions that I have provided.  Quasar is excellent and should be a great replacement for Quickbooks.  

The thing that is so tough about Linux is the stuff that works is easy, but once you run into a problem it can be very difficult.

---

### Post by jonny on 2007-12-08
I wrote the wiki entry that you referred to - sorry that you found trouble using it.  I reinstalled Quasar myself a few days ago using the wiki and it definitely does work on Ubuntu 7.10 provided that you follow all of the instructions exactly to the letter.

What is the exact error message that you're getting when you try to install Sabot's version of Quasar?  I'm surprised that you're getting any conflict, as it sounds as if you weren't able to install Quasar using my instructions.  If you did somehow manage to install it, removal isn't completely straightforward: you need to delete the folder /opt/quasar, remove the quasar user and remove the file /etc/xinetd.d/quasar.  According to how far you got, you might also need to remove the menu entries that you created in /usr/share/applications, drop  the newly created PosgreSQL users and drop any PostgreSQLdatabases that Quasar created.  Some of these things need root permissions but I'm hesitant to cite code as, if you badly cut and paste file deletion with root permissions, you could totally hose your system.

Without wanting to sound discouraging, though, I have a serious concern with what you're attempting to achieve here.  As an accountant, I really couldn't responsibly recommend that anyone should attempt to control the finances of a startup business with a complex unfamiliar accounting system on a complex unfamiliar operating system without any suport.  How would you manage if some ubuntu upgrades meant that Quasar no longer ran on your system?  How will you manage backups and recovery if you're not familiar with the PostgreSQL database on which Quasar runs?  Will you know what to do if you run into performance issues as your database fills up?  Quasar is a full-featured, complex accounting package that takes time for an experienced bookkeeper to master - are you sure that you have the background?  Surely you want to concentrate on running your business, not learning how to install and support an accounting system.

If you're betting your business on Quasar, you need to be confident and competent at troubleshooting Linux and PostgeSQL - and that means doing some serious studying.  Both Linux and Postgres are immensely powerful but the cost of that power is enormous complexity and a steep learning curve if you want to do anything more than simple pointing and clicking.  A possible solution for you might be to use an application supported by Canonical (for example, GNUCash) or to take commercial support from Linux Canada or one of their resellers.  However, my understanding is that they only support Quasar on Red Hat or SUSE, so that option knocks out Ubuntu as your operating system, and I have no idea what they might charge - which I imagine would be of great concern to you at this stage of your business's development.

---

### Post by art.by.bec.com on 2007-12-10
Thanks for all your generous info and concern.
I think you are correct in regard to running a business and not knowing linux well enough.
I felt forced to try though, because my old computer which i have been using with quick books is unstable now. The new computer is on vista and as i said... trying to force me to upgrade all the programs. I also have a friend who is very experienced with ubuntu who said he would help me, but has been too busy lately.

I think though, i will go back to the old computer and keep learning linux

Thank you very much
bec

---

### Post by art.by.bec.com on 2007-12-10
[ATTACH]52819[/ATTACH]

this is the error i get...

---

### Post by art.by.bec.com on 2007-12-10
Update

I played around with Sabot's suggestions and wacko...
quasar is up

thank you so much for your help Sabot and Jonny
i still want to try and keep learning, even though i agree that it is dangerous to do the bookwork on an operating system that i am unsure about.
thank you 
bec

---

### Post by art.by.bec.com on 2007-12-10
I have just been looking at quasar
i have looked at every conceivable accounting program for linux over the last 2 months
and i must say that quasar looks grea
simple easy to understand and similar to what i am used to
if i was careful to make back ups, i'd love to use quasar
what do you think Johnny?
bec

---

### Post by intoweb on 2007-12-14
Hi there. 

FYI: I\ve also just built a quasar deb for 7.10 by following instructions googled.
Iincluding use of "dh_make" and "debuild"
(the source tgz includes script to build rpm packages, which I previously used for opensuse10.1-3, however since I am testing kubuntu gutsy, I thought I'd give debs a bash.)

I've used Quasar significantly and know of others who use the commercial releases of Quasar too, and are generally well satisfied with it. It has great features and is more advanced than gnuCash. I've heard rumours that there will soon be a v2 commercial release. So if you want to support Linux apps and developers, then it would be money well spent. Great app!

The PDF manuals from [Linux Canada]("http://www.linuxcanada.com") are worth getting, coz they explain step by step how do everything. (and having them available offline means you don't always have to google for help).

regards

zerlgi3  :)  _-(at)_- myrealbox{D0t} com

---

### Post by John Jason Jordan on 2007-12-14
I can't get it working. I followed the instructions at the start of this thread, but I had to use dpkg -i --force-architecture because I use Gutsy x86-64. It installed OK and the rest of the command line things worked OK, and it created launch items, but neither Quasar nor Quasar - Admin will launch. From the command line both give me the following error message:

jjj@Devil7:~$ /opt/quasar/bin/quasar
/opt/quasar/bin/quasar: error while loading shared libraries: libtcl8.4.so.0: cannot open shared object file: No such file or directory
jjj@Devil7:~$ sudo /opt/quasar/bin/quasar_setup
/opt/quasar/bin/quasar_setup: error while loading shared libraries: libtcl8.4.so.0: cannot open shared object file: No such file or directory

I looked in Synaptic for libctl8*, but nothing showed up, and I have all the repositories enabled. I'm guessing it's a 32-bit library that is not installed. 

I really want to try Quasar! Any suggestions welcome!

---

### Post by jonny on 2007-12-15
> **John Jason Jordan said:**
> but I had to use dpkg -i --force-architecture

Unfortunately that generally won't work for packages built from programs written in compiled languages.  On a 64 bit system you don't really have any alternative but to build Quasar from source.

Did you try following the Wiki instructions?  If so, where did things go wrong?

---

### Post by jonny on 2007-12-15
> **art.by.bec.com said:**
> 
if i was careful to make back ups, i'd love to use quasar
what do you think Johnny?
bec

It's a tough call that depends on how you'd cope if you lost your system altogether.  If you have limited transaction volumes and keep printouts of the entries you load onto Quasar, the risk might be minimal.    The question that you need to ask is what you'd do if your PC failed.  Could you be confident that you could get a replacement, install ubuntu onto the new hardware, reinstall Quasar and restore your files.  If that's not a problem to you, go ahead.  If you have any doubts, hold back.

---

### Post by SatManUK on 2007-12-16
I have followed the Wiki to the letter .. 
I have Quasar Admin talking to PostGreSQL ok.. 
But when i try to login using Quasar itself it says Quasar Server is not running.

Any suggestions?

---

### Post by jonny on 2007-12-17
> **SatManUK said:**
> I have followed the Wiki to the letter .. 
I have Quasar Admin talking to PostGreSQL ok.. 
But when i try to login using Quasar itself it says Quasar Server is not running.

Any suggestions?
Presumably you mean that the Test button on the PostgreSQL Driver Config screen in Quasar Setup returns a positive result, but that the login screen for the Quasar client can't find the service.

Are you running a firewall?  If so, disable it and try again - unless you've told it otherwise, Quasar needs access to port 5432.  Another posibility is that your xinetd settings have become corrupted due to multiple failed installation attempts (this has happened to me before) and that the Quasar daemon isn't starting up.  To test this theory, try starting the daemon by hand and try again.
```
sudo /opt/quasar/bin/quasard
```
If it is your xinetd settings, you might have to hand craft the files in /etc/xinit.d/.  This is what's in my /etc/xinet.d/quasar:
```
service quasar
{
        type = UNLISTED
        flags = KEEPALIVE
        socket_type = stream
        port = 3599
        wait = no
        user = quasar
        group = quasar
        instances = UNLIMITED
        server = /opt/quasar/bin/quasar_clientd
#       server_args = -debug
        log_on_success += USERID
        log_on_failure += USERID
        disable = no
}
```

---

### Post by Sabot on 2008-02-07
When I create this deb file I made it warn you if you have quasar already installed.  This is the error that you are seeing.  It means that Quasar is installed!

> **art.by.bec.com said:**
> [ATTACH]52819[/ATTACH]

this is the error i get...

---

### Post by Sabot on 2008-02-07
My package is made for 32 bit and not 64bit.

> **John Jason Jordan said:**
> I can't get it working. I followed the instructions at the start of this thread, but I had to use dpkg -i --force-architecture because I use Gutsy x86-64. It installed OK and the rest of the command line things worked OK, and it created launch items, but neither Quasar nor Quasar - Admin will launch. From the command line both give me the following error message:

jjj@Devil7:~$ /opt/quasar/bin/quasar
/opt/quasar/bin/quasar: error while loading shared libraries: libtcl8.4.so.0: cannot open shared object file: No such file or directory
jjj@Devil7:~$ sudo /opt/quasar/bin/quasar_setup
/opt/quasar/bin/quasar_setup: error while loading shared libraries: libtcl8.4.so.0: cannot open shared object file: No such file or directory

I looked in Synaptic for libctl8*, but nothing showed up, and I have all the repositories enabled. I'm guessing it's a 32-bit library that is not installed. 

I really want to try Quasar! Any suggestions welcome!

---

### Post by tenoca on 2008-02-27
ok, this worked ok, but i cannot create a new company, any ideas?
never mind, I had to sudo run it, btw, I am installing this remotely, any hope of getting a deb to only install the client?

---

### Post by Sabot on 2008-02-27
> **tenoca said:**
> ok, this worked ok, but i cannot create a new company, any ideas?
never mind, I had to sudo run it, btw, I am installing this remotely, any hope of getting a deb to only install the client?

Sorry I am not really sure how to break them up.

---

