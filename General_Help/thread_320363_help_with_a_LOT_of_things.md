---
title: "help with a LOT of things"
date: 2006-12-17
forum: General Help
---

### Post by Jungle-Cat on 2006-12-17
Ok, im a total linux nub...kep that in mind. im setting up a mangos wow server; but b4 i get to that, i need hel pwith some basics first.

i need a step by step guide on how to get SAMBA going to be able to share files between my linux system, and my main windows system. I have ip's setup, and the linux sys is on the net. (so ive done somthing right). I cant work out how to install samba, tried a few guids but all failed. Ive got synapitcpackge manager installed, whihc was with ubuntu.

i also need a nub guide to installing a LAMP server (i assume u all know what that is, if u dont: Linux Apache Mysql PHP, basically a web server. I need somethinf which has all those configured together, or a detiled guide on how to get all that up.)

but for now i need samba fully going and functional with my windows system.

please help,
Jungle-Cat

---

### Post by maxamillion on 2006-12-17
[www.ubuntuguide.org](www.ubuntuguide.org)

start there, then ask here if you run into any issues

---

### Post by padre999 on 2006-12-17
Maybe this will help you with setting up SAMBA: 

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605) 
and 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ayoli on 2006-12-17
you may want to read that:
LAMP:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
SAMBA:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Jungle-Cat on 2006-12-17
ive tried that, it tells me to do some stuff in the terminal, i try it all! but i just get stuff with dependiencis...i really need an autopakcage or something. why does linux have to be so hard?

so, back to square 1. i cant install samba. i need to dl a package which has all dependencies i think, then install it all with something. or solve the problems...

*edit* i think ive found a jungle-cat friendly way to do it...ive opend up synaptic manger, and searched for samba. I marked for dl samba, samba doc's. Then clicked somewhere to start getting...now its downloading...is this right?

---

### Post by padre999 on 2006-12-17
> **Jungle-Cat said:**
> 
*edit* i think ive found a jungle-cat friendly way to do it...ive opend up synaptic manger, and searched for samba. 

It says this at the very beginning of the guide :-? ```
sudo apt-get install samba
``` does exactly what you are doing with synaptic now.

---

### Post by ayoli on 2006-12-17
there is nothing hard, for command lines use copy and paste.

---

### Post by Jungle-Cat on 2006-12-17
ok anyway...installing SAMBA like that didnt help...

however; it may have helped without me knowing. Ive gone to a network area, and gone to "add server" selected windows, put in share name as C$ (my c drive's shareing name) and gone to connect (put in my windows box ip and all that...) and it says cnat connect to smb://[randomcrap inc share name etc]

i assume smb is SAMBA...so...do i need to install a samba server on my windows box?? (atm im trying to copy stuff from windows - linux, where linux is client and windows is host)

i'll come back to lamp later...


Jungle-Cat

---

### Post by ayoli on 2006-12-17
no you dont have to install anythging on windows to use samba.
simple and graphical way:
open a nautilus window (gnome file explorer) go to file menu select 'connect to a server' (or you can reach that from panel Places menu also)
a window pops up, select wnidows share, file the fields.
you might be prompted for a password if the share is protected.

---

### Post by PilotJLR on 2006-12-17
Installing samba like that does help, as that is the correct way to accomplish it. Since you have no knowledge of what you're trying to do, it would be extremely beneficial to read the online guides, as mentioned before. If you start randomly changing things without understanding what you're doing, you'll only make it harder in the long run!


> **Jungle-Cat said:**
> ok anyway...installing SAMBA like that didnt help...

however; it may have helped without me knowing. Ive gone to a network area, and gone to "add server" selected windows, put in share name as C$ (my c drive's shareing name) and gone to connect (put in my windows box ip and all that...) and it says cnat connect to smb://[randomcrap inc share name etc]

i assume smb is SAMBA...so...do i need to install a samba server on my windows box?? (atm im trying to copy stuff from windows - linux, where linux is client and windows is host)

i'll come back to lamp later...


Jungle-Cat

---

### Post by Jungle-Cat on 2006-12-17
well i did the samething i did last night, however i left a field blank (which iddnt seem necesary) and it works great now!!!! thanks guys...now, how do i do the same, but use windows as the client and linux as the host?

*edit* my linux desktop still has the icon for the one that doesnt work, which i made last night. how can i del the icon? im lost :S

*edit again* trying to isntall wine using [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) under the synaptic guide...its asking for dependancies and refuses to install. So...(i just disc. that im not using 5.1 breezy, im using 2.06 hoary hedgehog or something, is this a problem?)

*another edit* can some1 provide a simple way to remote into the linux box from windows?

*edit (QUICK FIX THIS ONE)* following [this guide]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-59bdeb1f6438eddbde544b41ca0a5149c59624b6") im up to setting up mysql stuff; now im quite confident with this step as ive done similar b4 in windows. But im stuck; doing the command to make a general, default config doesnt work (command invlaid/not found) can some1 post a fix for this?

---

### Post by ayoli on 2006-12-18
> **Jungle-Cat said:**
> well i did the samething i did last night, however i left a field blank (which iddnt seem necesary) and it works great now!!!! thanks guys...now, how do i do the same, but use windows as the client and linux as the host?
go to menu System>Administration>Shared folders.
add a new share if there is none, then pick the Prperties tab and check that the domain/workgroup name is the same as your windows machine. then from windows browse your network neighborhood
> **Jungle-Cat said:**
> 
*edit* my linux desktop still has the icon for the one that doesnt work, which i made last night. how can i del the icon? im lost :S
if you mean an icon made with "Connect to a server", then right clik on it and select "umount volume".
> **Jungle-Cat said:**
> 
*edit again* trying to isntall wine using [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) under the synaptic guide...its asking for dependancies and refuses to install. So...(i just disc. that im not using 5.1 breezy, im using 2.06 hoary hedgehog or something, is this a problem?)

why dont you just try in a terminal (open a terminal or console from menu applications>accessories>terminal):
```
sudo aptitude install wine
```
(sudo command will prompt you for your **_user password_**, requiered for admin tasks)
you may want to read [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
> **Jungle-Cat said:**
> 
*another edit* can some1 provide a simple way to remote into the linux box from windows?
[https://help.ubuntu.com/community/VNC#head-d5c9bb061a40af00cf3c664dfb702a9ca3b0baf8](https://help.ubuntu.com/community/VNC#head-d5c9bb061a40af00cf3c664dfb702a9ca3b0baf8) and then search for a vncviewer app for windows and use it to connect to your win box.
> **Jungle-Cat said:**
> 
*edit (QUICK FIX THIS ONE)* following [this guide]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-59bdeb1f6438eddbde544b41ca0a5149c59624b6") im up to setting up mysql stuff; now im quite confident with this step as ive done similar b4 in windows. But im stuck; doing the command to make a general, default config doesnt work (command invlaid/not found) can some1 post a fix for this?
nothing hard here, what have you done ?
just type in a terminal:
```
sudo aptitude install mysql-server libapache2-mod-auth-mysql php5-mysql
```

---

### Post by Jungle-Cat on 2006-12-18
apache and php is all working great (unless php-mysql communication isnt wokrign but i cant try that yet). ive got it all installed, but to get mysql going , i need a deafult config file. Which isnt there...so all i need is a config file for mysql.

---

### Post by ayoli on 2006-12-18
check file /etc/php5/apache2/php.ini you must have this line without ';' at begining:
```
extension=mysql.so
```

---

### Post by Jungle-Cat on 2006-12-18
ok but first i need mysql up so i need a config..if anyone ahs 1 can u post it somehwere please?
i tried google with no success

call me an idiot; but that vnc guide made no sense to me...can u post all the apps and installation i need for that? rember i need to use windows to view linux :)

i'll try wine now...
*edit* crap...it asks for a long list of dependencies, i thought synaptic was suppsoe t odownlaod all those for me, when i ask to install wine...

im having trouble connecting to ubuntu to view files, from my win box. i ask to connect to \\192.168.1.137\FS$ where FS$ is the name of the sahre, which is file system. it brings up the "connect ot ubuntu" i enter root as my password and my root password as the password; but rejects the login. what am i doing worng? do i have to amke a sharing sort of account in linux?

---

### Post by ayoli on 2006-12-18
mysql conf file is here: /etc/mysql/my.cnf but there is no particular need to edit it
to run mysql if it's not already launched type in a terminal:
```
/etc/init.d/mysql start
```

---

### Post by Jungle-Cat on 2006-12-18
i tried again and it worked =D stupid 5 dollar keyboard...buttons dont work. but i sahll not fear, for i am getting a new keybaord for xmas, and will plac ethis keybaord on the penguin box. ok brb...setting up sql now

*edit* oh noes i cant find the bind-address thing...i to change it so i can read/write to sql db from win with navicat. also i dont have a desk for this server so thats why i need to setup vnc  fairly soon...my back hurts...im gonna copy over the config to win, cos this monitor doesnt burn my eyes as much :S *edit* there is no bind-address in it! oh noes! maybe it will let me remotly access sql anyway..will try now. doesnbt work; i cant find the bind-address seting please help cos this is an important stting which i need to change

im still stuck with file sharing; with windows as client and ubuntu as server. my share is the filesystem, and the sahrename is FS$. so i go to (in win explorer) \\192.168.1.137\FS$. i get a login screen, so i put in root [pass]. only problem is that doesnt work...is there another username and pass somewhere?

---

### Post by Jungle-Cat on 2006-12-18
uve all nelgected me :( i'll bumd the topci then =D

ive tried setting up SMF, a forum that uses mysql and php. as soon as i enter the php installer, this is the error i get:

"The installer was unable to detect MySQL support in PHP. Please ask your host to ensure that PHP was compiled with MySQL, or that the proper extension is being loaded."

the php i have installed is 4, so i went into a termianl and entered
[c]sudo aptitude php4-mysql[/c]
then i restarted ubuntu, but it still doesnt work. i'll try using the terminal and reinstall LAMP, without using synaptic. (therefor php5 :) )

*edit*ok reinstalled it all; setting up now.

installing wine...it says unmet dependencies. gives a list of things...however they are all installed. so why wont wine install?

*edit*well im a dumbarse. i forgot to allow php-mysql communication, like wat ayoli said editing php.ini. Now...to start over yet again (i tried using terminal but it didnt install all the other things i think...ok ive got it going now i think; but where do i change permissions? not even locahost can read files :S

*edit*
**how to get game server running**
its got 2 binaries, 2 configs (same as win version). both neeed to run, but how do i start the binaries? navicat was easy to run, it had a binary, but also a script that was called start-navicate. [rapidshare download for start-navicat]("http://rapidshare.com/files/8076453/start-navicat.html") is there a way to make something like that? or how do i run a binary?? there isnt a .deb or anything, just binaries, sql entries, and configs, very straight forward. *edit* ive been looking around and i think u can install it form the tar, therefor ubunt knows its an isntalled program (?). can someone explain how to do this (where to put the tar.gz to where and run what ccomands) thanks

---

### Post by Jungle-Cat on 2006-12-19
oh god no one is answering me...

anyway mysql jsut wont work. by default it has o pass, so u use "root" and no password. i cnat change my pass in the terminal. when i try connecting with navicat from localhost i get a (111) error.

wats going on??

---

### Post by koenn on 2006-12-20
```
wats going on??
```
you jump from one thing to another, "oh no now this ... " oh no now that ..", you try to do 4 things at once while the first rule in troubleshooting is 'don't add to the confusion, solve the problem before you add something new', you leave out important information (like : when you say "doing the command to make a general, default config doesnt work (command invlaid/not found) can some1 post a fix for this?" it would be helpful if you actually mention which command you typed in. Even better: "cant connect to smb://[randomcrap " - if it can't connect, it would at least be interesting to see what the "random crap" was, it's probably not as random as you think), and between all that you expect others to keep track of what you're trying to accomplish, what you have done, figure out what the real problem is behind al thye gibberish, and try to think of a sollution. 
You're not really making things easy for those you're expecting to help you.

---

### Post by koenn on 2006-12-20
```
call me an idiot; but that vnc guide made no sense to me...can u post all the apps and installation i need for that? rember i need to use windows to view linux 
```
I will not call you an idiot, because that's against ubuntu forum policy, but that 'guide' consists of 2 easy 'click here, click there' instructions. 
Exactly which of the following is it that you don't understand ?
> 
System > Preferences > Remote Desktop
          'Check' the first two boxes to activate the service:
                Allow other users to view your desktop (view only)
                Allow other users to control your desktop (view & control).

           Below you can set security. The two options are:
                Ask you for confirmation 
                       (ie; someone at the machine must click OK to grant remote access)
                Require the user to enter this password: 
                      This is ALWAYS a good idea. 


you need a 'vnc client'  for your windows. look on the web for tightvnc, realvnc or so.
(in case that sentence did not make sense : click on this link:
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html) 
)

---

### Post by Jungle-Cat on 2006-12-21
i worked that out; the thing i didnt know is that it used VNC. Ive got that all up...yeah i guess i have jumped around a bit so i'll post all my problems again:

**LAMP**. I've got all but Mysql setup. i get "1130 '192.168.1.21' is not allowed to connect to this mysql database" erros. i have hashed out the like "skip-networking" in the my.cnf file. I need to be able to access mysql from my win box.

**Binaries** I have a simple program which has "bin, lib, etc" folders. I assume i copy those to file system....so i did that. So how do i run a binary? (they use mysql, so mysql is a higher priority)

I apologise for being confusing and making another thread...

---

### Post by koenn on 2006-12-21
> **Jungle-Cat said:**
> 
**Binaries** I have a simple program which has "bin, lib, etc" folders. I assume i copy those to file system....so i did that. So how do i run a binary? (they use mysql, so mysql is a higher priority)

A binary is just a program, you can run it any number of ways (command line, launcher, ...)
most programs have some associate files in /bin, /lib; /etc etc. 
Normally you shouldn't have to copy files by hand - most programs have an installer script that installs the program, puts files where they belong, and so on. If you install using synaptic, it's all taking care of and you get menuitems to launch the program automatically. 
So, 
1- exactly what program are you talking about ? 
2- where did you get it and why did you not install it via System : Administration : Synaptic

---

### Post by koenn on 2006-12-21
> LAMP. I've got all but Mysql setup. i get "1130 '192.168.1.21' is not allowed to connect to this mysql database" erros. i have hashed out the like "skip-networking" in the my.cnf file. I need to be able to access mysql from my win box.

give us something to work with :

1- is 192.168.1.21 the address of your windows box ?
2- what's the address of the computer running msql ?
3-  did you set up user accounts in the mysql database, like
```
mysql> grant all privileges on *.* to <userName>@<hostName> identified by 'passwrd'
```
([http://forums.mysql.com/read.php?34,34957,92295#msg-92295](http://forums.mysql.com/read.php?34,34957,92295#msg-92295))
4- which command or program produced the "1130 '192.168.1.21' is not allowed to connect to this mysql database" error ?
5- do you know with which user account this command or program was executed ?

---

### Post by Jungle-Cat on 2006-12-21
ok thx, i'll try this later on, 2am over here in australia.

192.168.1.21 - win box
192.168.1.137 - ubuntu box

no i havnt setup accounts yet; im trying to use "root" <no password> (mysql)

so i'lll try all that later on, this morning whe ni wake up xD

---

### Post by Haegin on 2006-12-21
Ok - you said you are using 2.06 Hoary or whatever - that is a VERY bad start as its about 4 years out of date and the latest version is 6.10 - Edgy which comes with a LAMP install disc here:
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
You need the server install cd  then follow this guide to get up and running
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

Once you have done that then concentrate on getting VNC working - you know how now and then come back with everything else you want to do one at a time and concentrate on each in turn. Don't try and do everything at once and come prepared to learn.

---

### Post by Jungle-Cat on 2006-12-21
ive got VNC going.
Here in aus internet isn't exactly cheap so ive only got 25gb a month, and ive got to share that with my bro and father. and where a bit ahead at the moment...im considering getting some shipit discs sent here. (the ones im using were shipit, my bro got them.)

Im using **5.04** Hoary Hedghog.

i think ive got LAMP going; just mysql is not going for me. When i shutdown ubutnu it says "shtting down mysql database "mysqld"" so mysql is runnning and going. I just cant seem to access it.

trying to do
```
mysql> grant all privileges on *.* to <userName>@<hostName> identified by 'passwrd'
```
nothing happens. Im logged in as root (mysql root and ubutu root). i just get a -> prompt. ie:

mysql> grant all privileges on *.* to deaglan@deaglan identified by ''
       ->

thats what happens. (i have not yet setup a mysql password)

oh and heres the program im trying to use:
[http://rapidshare.com/files/7990800/Mangosd_2838_Linux.tar.gz](http://rapidshare.com/files/7990800/Mangosd_2838_Linux.tar.gz)

i'd appreciate if u didnt ask wat it is :)

---

### Post by Jungle-Cat on 2006-12-22
bump

---

### Post by Haegin on 2006-12-22
You need a little patience - you bumped after only 6 hours - remember people are in different time zones - I was asleep when you posted and still asleep when you bumped...

You need to get the latest version of the OS otherwise you are banging your head against a brick wall - cant you spare even one gb of 25 to download a 700mb cd? 25gb is a lot unless you are downloading a heck of a lotta illegal movies and stuff. pr0n...tut tut tut...
Dapper was much better than breezy and edgy is better than dapper so for the sake of 700mb get the cd and use that guide i gave you.

---

### Post by ayoli on 2006-12-22
> **Human Prototype said:**
> You need a little patience - you bumped after only 6 hours - remember people are in different time zones - I was asleep when you posted and still asleep when you bumped...
 +1
[http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)
[http://ubuntuforums.org/showthread.php?t=303716](http://ubuntuforums.org/showthread.php?t=303716)
> **Human Prototype said:**
> 
You need to get the latest version of the OS otherwise you are banging your head against a brick wall - cant you spare even one gb of 25 to download a 700mb cd? 25gb is a lot unless you are downloading a heck of a lotta illegal movies and stuff. pr0n...tut tut tut...
Dapper was much better than breezy and edgy is better than dapper so for the sake of 700mb get the cd and use that guide i gave you.
+1

---

### Post by Jungle-Cat on 2006-12-22
like i said i have to sahre with my family and they download a lot.
and css crunches a bit of usage.

so can you pelase stop telling me to update...

---

### Post by Haegin on 2006-12-22
Well you arn't really going to get anywhere without that server install cd which lets you do a specific LAMP install - you are struggling up hill unnecessarily. If you want help you need to be able to do what people suggest as a solution - I have set up a LAMP server of my own on ubuntu dapper and as I understand it is similar on edgy but when I tried on pre dapper versions of ubuntu it was a lot harder.

Stop making more work for yourself.

---

### Post by Jungle-Cat on 2006-12-22
if i can get this going a bit i may update ubuntu at the end of my billing month. (early next month) but b4 i do that i need to know that this mangos thin works. so can u atleast tell me how to launch that to see if i can get it going, or r u just gonna ask me to update and use the run-binary install disc?

---

### Post by koenn on 2006-12-22
> **Jungle-Cat said:**
> 
i think ive got LAMP going; just mysql is not going for me. When i shutdown ubutnu it says "shtting down mysql database "mysqld"" so mysql is runnning and going. I just cant seem to access it.

sounds good. run
```
 /etc/init.d/mysql restart 
```
to verify that mysqld starts error-free

> trying to do
```
mysql> grant all privileges on *.* to <userName>@<hostName> identified by 'passwrd'
```
nothing happens. Im logged in as root (mysql root and ubutu root). i just get a -> prompt. ie:

mysql> grant all privileges on *.* to deaglan@deaglan identified by ''
       ->

ok  - you should end the statement with **;**
```
mysql> grant all privileges on *.* to <userName>@<hostName> identified by 'passwrd' **; ** 
```


other than that : I agree it would be better to upgrade (to Dapper - I have my doubts about Edge) : there have been lots of improvements (and probably fixes) in Apache, php and Msql + the packages that glue them together so working with older versions is making it harder on yourself. Still, if you insist on sticking with Hoary for the time being, at least you'll know where all the config stuff is by the time you upgrade :-)

---

### Post by Jungle-Cat on 2006-12-22
Everybody koenn is awesome.
Human Protype is not.

yay i can now access the mysql databsae =D

now i need to run those binaries...

*edit* hmm some problems...trying to use navicat in windows im being told syntax is not right, (finsihed unsuccesfully), and with anther thing im being told succes but all the tables arn't showing up. anything else i need to allow remote writing to the mysql serveR?

*edit* it may help if i have the latest mysql...if it doesnt cause any problems, can someone tell me where the mysql 5 repositories are?

---

### Post by Jungle-Cat on 2006-12-23
I've come to a..err...hmmm...revolution?
ive devided not to run that whole mangos thing, instead make the box a linux web and media server. Im gonna use the GeexBox media linux distro as the player, and ubuntu as the general file management and storage, transfer.

However, i'd still like to know how to get mysql all going. Dont bother explain binaries to me, unless its a quicky.

---

### Post by Haegin on 2006-12-23
> **Jungle-Cat said:**
> 
Human Protype is not.


Oh please, at least spell my name right!

---

### Post by Jungle-Cat on 2006-12-23
H - for human
U - for umbrella
M - Mother
A - Apple
N - Negativly charged proton

P - Peanut
R - Richard
O - Orange
T - Timber mill
O - Olive
T - Tooth
Y - You
P - Peanut butter jelly
E - Elephantitis

:) i can spell :)

---

