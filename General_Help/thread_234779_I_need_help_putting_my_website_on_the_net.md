---
title: "I need help putting my website on the net"
date: 2006-08-12
forum: General Help
---

### Post by CameronCalver on 2006-08-12
Hello i am a n00b at webpages but i have created a simple one but i do not no how to do it at all.
I would like to have it on ftp or http maybe using my ip address or a dot tk account
I would like to use screm with this

---

### Post by aysiu on 2006-08-12
You're going to make your own computer into a web server?

---

### Post by CameronCalver on 2006-08-12
no i was thinking that i could have the website on if i wanted to send someone a file eg
have a simple website that says like
games,app,doc, etc  and then in the night i'll turn the comp off and the website will not be accessable but as soon as i boot my comp up it will be on the net again
Is that possible?

---

### Post by scxtt on 2006-08-12
**sudo apt-get install apache2**
put files in /var/www
forward port 80 (if you have a router)
tell people your IP

there's some other steps involved, but not much point explaining them til you're too that point ...

---

### Post by Greycloak on 2006-08-12
Your ISP will not be happy with you.  Try searching for some free/cheap web hosts.

---

### Post by CameronCalver on 2006-08-12
my isp said this
upload the files to
```
ftp://calvershome@iinet.net.au
```
and view them at
[http://www.iinet.net.au/~calvershome](http://www.iinet.net.au/~calvershome)
but i dont no how to upload

---

### Post by scxtt on 2006-08-12
bah, any respectable cable ISP isn't gonna flinch if you're hosting files ... maybe if you're trafficking an exuberant amount of large files, you'd be in for a letter - but even that is a stretch ...

having your ISP host the files (which is what [http://www.iinet.net.au/~calvershome](http://www.iinet.net.au/~calvershome) would be) is different from having your own apache server ...

---

### Post by CameronCalver on 2006-08-12
ok then i did what you said about apache2 but im not sure how to port forward im using a zyxel prestige 660

---

### Post by CameronCalver on 2006-08-12
ok i found out how to port forward but it says
Start Port                End Port                Ip address

---

### Post by scxtt on 2006-08-12
well, if that's a router - look for something that refers to HTTP or specifically port 80 ... it shouldn't be hard to do ...

start port: 80
end port: 80
IP address: local IP address (like 192.168.1.100)

---

### Post by CameronCalver on 2006-08-12
ok well i have put in my router 
start port 80 end 80 and ip 192.168.1.102 (thats my ip) and when i go to
 [ftp://203.217.88.100](ftp://203.217.88.100) or [http://203.217.88.100](http://203.217.88.100) it does not work u try it to see if it works

---

### Post by scxtt on 2006-08-12
do you have any files in /var/www ... ?  do you have a firewall?

make an index.html file (/var/www/index.html) -- you can just type **this is a test** in it ...

you can test it locally, but using either [http://192.168.1.102](http://192.168.1.102) or [http://localhost/](http://localhost/) ...

---

### Post by CameronCalver on 2006-08-12
yes they both work and say 
this is a test
so that is good but i dont think i have the port forwarding this right lookat the screen shots
[http://img96.imageshack.us/my.php?image=screenshotes3.png](http://img96.imageshack.us/my.php?image=screenshotes3.png)
and
[http://img96.imageshack.us/my.php?image=screenshot1sb4.png](http://img96.imageshack.us/my.php?image=screenshot1sb4.png)

---

### Post by scxtt on 2006-08-12
i'm not sure what any of that stuff in the 1st screenshot means, my router isn't like that, but try setting it to "full feature" and/or posting what's under "Edit details" ...

---

### Post by CameronCalver on 2006-08-12
ok this is the screen shot of edit details on full feature
[http://img209.imageshack.us/my.php?image=screenshotqb6.png](http://img209.imageshack.us/my.php?image=screenshotqb6.png)

---

### Post by scxtt on 2006-08-12
that doesn't seem like it should apply, looks like specific rules to filter IPs ...

if it's not working, all i can think of is that your ISP blocks port 80, which can most likely be circumvented by using a different port (edit the line in /etc/apache2/ports.conf -- set it to something else - maybe 6500 {not sure if it matters what the # is} ... and also change that on your router {where it used to be 80} -- then it should be accessible via http://<ip-address>:6500 ...

---

### Post by CameronCalver on 2006-08-12
nope now i cant even get it localy is there any other way besides port forwading

---

### Post by scxtt on 2006-08-12
did you restart apache after making the change?  i changed mine to 6500, restarted apache and entered **[http://localhost:6500/~scxtt/index.html](http://localhost:6500/~scxtt/index.html)** and got what i expected ...

**sudo /etc/init.d/apache2 restart**

and you have to port forward, because when a request hits your router, it needs to know what box to forward a request on a port to ...

---

### Post by CameronCalver on 2006-08-12
ok i restarted apache2 and when i go
http;//192.168.1.102:6500 i get my test page so now what next

---

### Post by scxtt on 2006-08-12
well, you're good to go now (i could see your "hey this is a test" page) ... so you can move any files (and directories) you want to share into /var/www and give people the address ... so if you put pictures.tar into /var/www --> /var/www/pictures.tar ... you can give people the address [http://203.217.88.100:6500/pictures.tar](http://203.217.88.100:6500/pictures.tar) and they can download it ...

---

### Post by CameronCalver on 2006-08-12
Thank you so much for all your help you a welcome to visit my website any time and i will have a chat room one time and you can be mod if you would like but just one thing is there any way i can monitor my website to see if people are viewing

---

### Post by scxtt on 2006-08-12
you're welcome :)

you can take a look at **/var/log/apache2/access.log** to see apache hits ... there's also software out there that can present you with a nicer look (look for webalizer in the repos as an example) ...

---

### Post by CameronCalver on 2006-08-12
Hey i just put my proper website im making in/var/www and now i cant view it not even locally? wats hapening

---

### Post by scxtt on 2006-08-12
looking @ the source, it looks like it has to do w/ the fact that you're using absolute paths to your files, instead of relative ones, so if you're using an image (that was located @ /home/cameron/website/pic1.png) and you move everything out of /home/cameron to /var/www/website/pic1.png the source is wrong ...

---

### Post by CameronCalver on 2006-08-12
the problem was that in / var/www dir i had index.html and another .html so now i have it as index.html then a folder called pages then a folder pics etc but how come the pics dont come up have a look
[http://192.168.1.102:6500/](http://192.168.1.102:6500/)

---

### Post by scxtt on 2006-08-12
for the reason i said above ...

for example:

<img style="width: 67px; height: 67px;" alt="Ubuntu Logo" src="file:///home/cameron/random/website/cameron%27sWebsite/pics/ubuntu_logo.png">

should be:

<img style="width: 67px; height: 67px;" alt="Ubuntu Logo" src="pics/ubuntu_logo.png">

if the page that's requesting it is located at /var/www/ and you have a folder /var/www/pics in which ubuntu_logo.png exists ...

that's basically web design 101 stuff ... not related to apache ...

---

### Post by CameronCalver on 2006-08-12
Ok i scapped that one 
and created another index.html in /var/www and i cant access it can you try i think apache is very temperemental

---

### Post by scxtt on 2006-08-12
i can currently see "He is this working??" ...

and apache isn't really tempermental as much as it has rules you have to follow - you can control them - but you have to follow them ...

---

### Post by CameronCalver on 2006-08-12
ok tell me what it says now and if it does what address are you using

---

### Post by scxtt on 2006-08-12
i see "ok if it work just say it works kk"

remember, you can't use your "outside" IP locally ... to test it yourself, use [http://localhost:6500](http://localhost:6500) from your own browser, [http://192.168.1.102:6500](http://192.168.1.102:6500) from another box on your router and give your "outside" IP to others not on your network ...

---

### Post by CameronCalver on 2006-08-12
ok im setting up my main website now ill reply when im nearly finished basic web and thanks for all your help

---

### Post by CameronCalver on 2006-08-12
Ok look at the site now the pics are in /var/www and the index.html file is in /var/www but it show like there is not pics there

---

### Post by az on 2006-08-12
> **CameronCalver said:**
> my isp said this
upload the files to
```
ftp://calvershome@iinet.net.au
```
and view them at
[http://www.iinet.net.au/~calvershome](http://www.iinet.net.au/~calvershome)
but i dont no how to upload

Use nautilus.  Click on Location and enter the FTP address.  You will be asked for a username and password and you will then be able to drag and drop your files using nautilus (filemanager)

---

### Post by CameronCalver on 2006-08-12
lol a bit late now lol \
my website is [http://203.217.88.100:6500](http://203.217.88.100:6500)

---

### Post by Tomosaur on 2006-08-12
Very, very slow lol.

---

### Post by CameronCalver on 2006-08-12
So what is something that will give my website a nicer look
and what u meen so slow

---

### Post by Tomosaur on 2006-08-12
Your upload speed is very limited, so all your images and such take a long time to load. If you're hosting the website yourself, you should definately think about making it mostly text-based, or buy a better net connection which has faster uploads. As for downloads, you probably shouldn't even bother.
And also, learn CSS.

---

### Post by CameronCalver on 2006-08-12
ok i dont really care about internet speed because im only going to be sharing small files to and fro with my friends.
Also what is css and i would like a hit counter but i cant find one that works

---

### Post by CameronCalver on 2006-08-13
ok just a couple of things if i have a file i want to put on it how do i make a link to it and how do i put a hit conter on
Also im using nvu

---

### Post by Tomosaur on 2006-08-13
I have no idea what nvu is, but:

Put the file you want to share in the webpage folder. An ordinary link to the file will work just fine (the same kind of link you would use to link between pages), but if the file is a .txt file or something very similar, you may want to enclose it in a .zip file or something like that, since many browsers will just load the text file as if it were a web page.

A hit counter is basically useless, but if you want one, you can get them for free off many websites. Just type 'free hit counter' into google and follow the instructions when you find one you like.

CSS stands for 'cascading style sheet'. You don't really NEED it, but it helps your website look a lot nicer, and also saves on bandwith.

---

### Post by CameronCalver on 2006-08-14
Can someone tell me how to set up css in nvu

---

### Post by ProjectGod on 2006-08-14
i only read your second post so im pretty sure i'm repeating something someone's already said... but... i think you need to setup up an ftp server if you wish to only send files to / from friends. 

that way you (if you allow) you they can upload files and also download files. 

i've tried the windows equivalent of sftp (ssh + ftp) i'm certain sure theres one for linux. (obviously). personally the sftp is much more secure than normal ftp. 

in saying all this you still need to have a router (assuming you have broadband) that can forward ports to such as incoming TCP port 22 or 21 to a specified internal IP (your FTP server)...  furthermore if you have a static IP (public ip) given to you by your ISP its better. do a google on "what is my ip" to get your public IP. if it is dynamic (more likely) then you can check your ip everytime a friend needs to upload / download. and tell them your ip OR you can use DDNS 

[www.dydns.com](www.dydns.com)

this maps a userfriendly name to dynamic public ips. so all your firends have to do is [ftp://sample@dydns.com](ftp://sample@dydns.com) or something youchoose... the registration is absolutely FREE.

if you have a personal firewall set up like firestarter. make sure you allow for incoming ftp traffic. 

furthermore to secure the ftp or any other daemon / service running on your machine. edit the /etc/hosts.deny file so that all remote handling / request of services are explicitly denied. enter the following in /etc/hosts.deny

ALL: ALL

... and in your /etc/hosts.allow specify specific IP addresses of friends ... you may need to get their public ips as well... this is a pain but it's much more secure. 

enter as follows...

service: ipaddress

hope this helps.
cheers.

---

