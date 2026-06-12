---
title: "MySpaceIM"
date: 2007-03-23
forum: General Help
---

### Post by elephant007 on 2007-03-23
I have convinced my sister to try Ubuntu.  The only thing holding her back from trying it is the fact that she uses MySpaceIM.  I have downloaded the client and used WINE to install it, I ran it, put my username and password in and it attempts to connect, after a short while (a few seconds) it crashes.
oh yeah, Wine Gecko installs too.

```
[error title bar] MySpace IM Had To Quit. 
[description]Sorry, something unexpected happened and MySpaceIM had to quit. 
Cliick OK to restart MySpaceIM.  
```

I'm given the option to click OK and Cancel.  Either button I click MySpaceIM closes.
My question is, how can I find out what this "unexpected" error is and is there an alternative chat client that could be used that will connect to the MySpaceIM server(s)?

---

### Post by elephant007 on 2007-03-23
> Will there be a Macintosh or Linux version of MySpaceIM?

Mac and Linux users, we've heard your pleas and haven't forgotten you! During this beta phase, we are concentrating on working out the kinks in the PC version, and are assessing various options for providing IM to our Mac and Linux users, as well as eventually delivering IM on mobile devices.

you'd think that if they really wanted a Linux version they would release the information that's needed to connected to their IM server to the Linux community and let the Linux community come up with the program for them... right?

---

### Post by hikaricore on 2007-03-23
They used too many .NET and IE shortcuts in their "programming" so they don't want to look retarded.

There is currently no other way to run myspaceIM in any useable way, than directly in windows OR with VirtualBox or VMware.  I have it installed on my server's Vbox and use rdesktop to connect when need be.  :)  There is also as of yet no plugins for any of the other IM applications you may use in linux to connect to MyspaceIM.  I heard Trillian will be supporting this soon, but that's not very helpful either.

_my message to myspace:_ **lrn2code tom**


That is all.

---

### Post by elephant007 on 2007-03-23
thanks for your response and insight.  I was able to find out what the IP Address and Port number the MySpaceIM uses for connectivity.  I don't know whatelse is needed in order to connect to their server and chat.  
would it be possible to plug this information into an account created using GAIM? 

My sister complains of how slow her computer is running (Windows XP) and is open to the possibility of switching to Ubuntu.  I should first talk her into getting rid of MySpaceIM!!! HA HA

---

### Post by tnyspi on 2007-03-31
When I try to install MySpaceIM with Wine, it says it needs to download and install "Mozilla Active X" but it never does.

---

### Post by Shin2010 on 2007-08-10
Hi, sorry if replying to some thing old here. With myspaceIM I was wondering if its even worth going in pain with the Pidgin Protocol Plugin to get myspaceim to work, so far I have Pidgin install but I'm so new with linux, I'm getting the hang of it after being with windows for so long and dos. But to get to the point here I did half of what the read me said and was wondering if any one has done this, I think with the msiminstall has a typo 

gcc -shared -`pkg-config --libs pidgin` message.o myspace.o -o libmyspace.so

and in the file message.o myspace.o  are only message.c and h, myspace.c and h 

unless I am looking in the wrong file. :confused:

---

### Post by kelly.seay on 2007-08-10
I did this, and it worked perfectly.  
I have Pidgin 2.1.0 installed from the pollycoke repos, you can find that info in the repository section of the forums.
These instructions were pulled from the site:  [http://developer.pidgin.im/wiki/MsimInstall](http://developer.pidgin.im/wiki/MsimInstall) and updated for Pidgin 2.1.0 and misiprpl-0.13

apt-get install pidgin-dev
apt-get source pidgin
tar zxvf pidgin_2.1.0.orig.tar.gz
mkdir msimprl-0.13

cd msimprl-0.13
tar zxvf ../msimprpl-0.12.tar.gz
cd libpurple/protocols/myspace

gcc `pkg-config  --cflags pidgin ` -D PURPLE_PLUGINS -c message.c myspace.c -I../../../../pidgin-2.1.0/libpurple/  -I.

gcc -shared -`pkg-config --libs pidgin` message.o myspace.o -o libmyspace.so

sudo mv libmyspace.so /usr/lib/purple-2/

# the images would go in /usr/share/pixmaps/pidgin/protocols/

The only problem I had was that Pidgin would lock up on me.  I fixed this by turning off the setting that automatically changes your availability if you are idle for however minutes.

---

### Post by Shin2010 on 2007-08-10
Wow I was waaaay off, but thank you for that I was using 

apt-get install pidgin-dev

apt-get source pidgin

tar zxvf pidgin_2.0.2.orig.tar.gz

mkdir msimprl-0.12



cd msimprl-0.12

tar zxvf ../msimprpl-0.12.tar.gz

cd libpurple/protocols/myspace



gcc `pkg-config  --cflags pidgin ` -D PURPLE_PLUGINS -c message.c myspace.c -I../../../../pidgin-2.0.2/libpurple/  -I.

gcc -shared -`pkg-config --libs pidgin` message.o myspace.o -o libmyspace.so



sudo mv libmyspace.so /usr/lib/purple-2/



# the images would go in /usr/share/pixmaps/pidgin/protocols/

No wonder my head hurts :( but thats odd I haven't ran into your guide, ok thanks again :)

---

### Post by hanzomon4 on 2007-09-03
Myspaceim still isn't showing up as a protocal

---

### Post by toucher5 on 2007-11-09
I have attempted to log into myspaceim with pidgin the same way i do for myspace.com and it says that the password is wrong. any one have an idea as to why? could it be fixed on the cli or in the advanced options?:confused:

---

