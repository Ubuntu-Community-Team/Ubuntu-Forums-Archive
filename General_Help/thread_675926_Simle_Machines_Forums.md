---
title: "Simle Machines Forums"
date: 2008-01-23
forum: General Help
---

### Post by lenswipe on 2008-01-23
Hi there

I just downloaded simple machines forums (cos its free) and installed it on my webserver  using the webbased installer. At first it said that i didnt have MYSQL support so i installed MYSQL via command line using the sudo apt-get install MYSQL server command. After this  it  got to the next step in the installation but then asked me for a username, password, IP address and port number for my "FTP Server" seing as im going to be hosting the forum on a single machine at my house i gave it 127.0.0.1 for the FTP server IP and i gave it 21 for the port number and supplied the root username and password for those feilds. It then said something or other about not being able to connect to the FTP server with the details provided.

Has anyone got any ideas?

---

### Post by stalker145 on 2008-01-24
> **lenswipe said:**
> Hi there

I just downloaded simple machines forums (cos its free) and installed it on my webserver  using the webbased installer. At first it said that i didnt have MYSQL support so i installed MYSQL via command line using the sudo apt-get install MYSQL server command. After this  it  got to the next step in the installation but then asked me for a username, password, IP address and port number for my "FTP Server" seing as im going to be hosting the forum on a single machine at my house i gave it 127.0.0.1 for the FTP server IP and i gave it 21 for the port number and supplied the root username and password for those feilds. It then said something or other about not being able to connect to the FTP server with the details provided.

Has anyone got any ideas?

Have you installed FTP serve software? If so, make sure it's properly configured and then we can go from there.

---

### Post by lenswipe on 2008-01-24
> **stalker145 said:**
> Have you installed FTP serve software? If so, make sure it's properly configured and then we can go from there.

no i havent...

THANKS ILL DO THAT :D

(perhaps this would help :D)

what ftp software do you reccomend?

how do i install it??



ill keep yall posted of how i get along.

---

### Post by stalker145 on 2008-01-24
> **lenswipe said:**
> no i havent...

THANKS ILL DO THAT :D

(perhaps this would help :D)

what ftp software do you reccomend?

how do i install it??



ill keep yall posted of how i get along.

I don't generally use FTP, but just off the top of my head, I would say you could use ```
sudo aptitude install proftpd gproftpd
```The latter being a "Versatile, virtual-hosting FTP daemon" and the former being "[GTK+ configuration tool for proftpd]("http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29")" to make life easier if you aren't very familiar with the command line.

If anyone has any better suggestions, I'm sure they will be appreciated.

---

### Post by kool_kat_os on 2008-01-24
i use phpBB

---

### Post by lenswipe on 2008-01-24
> **kool_kat_os said:**
> i use phpBB

ok cool is it easy to setup?

---

### Post by kool_kat_os on 2008-01-24
Ya

---

### Post by lenswipe on 2008-01-24
> **kool_kat_os said:**
> Ya

im having issues with it - it tried to install it from terminal and it didnt work so i tried to install it thru synaptic and it didnt work either....

Heres what i got..

[IMG]http://i221.photobucket.com/albums/dd12/lenswipe/phpBBError.png[/IMG]

any ideas?

i actualy have something in the apache www directory already so should i maybe take that down?

Or Better still if you could tell me how to get that on the road....

---

### Post by kool_kat_os on 2008-01-24
Oh, srry you use it on linux, I used it on windoe'z.

---

### Post by lenswipe on 2008-01-25
> **kool_kat_os said:**
> Oh, srry you use it on linux, I used it on windoe'z.

hmmm...kk

Do you have Linux at all?

---

### Post by kool_kat_os on 2008-02-12
ya....i used to have linux on my server ......i have it on my desktop still

---

### Post by kool_kat_os on 2008-02-12
> **lenswipe said:**
> im having issues with it - it tried to install it from terminal and it didnt work so i tried to install it thru synaptic and it didnt work either....

Heres what i got..

[IMG]http://i221.photobucket.com/albums/dd12/lenswipe/phpBBError.png[/IMG]

any ideas?

i actualy have something in the apache www directory already so should i maybe take that down?

Or Better still if you could tell me how to get that on the road....

I downloaded it from phpbb website. It comes as the whole website and all of the files and you just put it in the apache directory

---

### Post by Bruneauinfo on 2008-02-16
okay, i've installed Simple Machines Forum before and you DO NOT NEED an FTP server to install it - at least not on your computer. the ftp server it is referring to is Simple Machine's Mothership ftp server, not yours. the problem is that you used 127.0.0.1 as your URL. unless you plan to have forum conversations with yourself I suggest you get a URL for your forum by registering one with a URL registration service like [www.DynDNS.org](www.DynDNS.org) and then set up your router appropriately to work with dynamic dns. since you already have a web server i'd say you've already done this. so the url you should be giving Simple Machines is the url of your webserver. however, since you'll probably want your web server's URL to take you to the web site you're hosting and not necessarily the forum then you'll need to specify the folder where the forum is installed on the URL you give simple machines.

for example: [www.mycoolwebsite.com/forum](www.mycoolwebsite.com/forum)

in this case the forum would be installed in a directory in your www folder called 'forum'.

btw i have a step by step guide on installing Simple Machines Forum somewhere in Ubuntu's forums. of course i installed it on Ubuntu 6.10

[http://ubuntuforums.org/showthread.php?t=331017](http://ubuntuforums.org/showthread.php?t=331017)

---

