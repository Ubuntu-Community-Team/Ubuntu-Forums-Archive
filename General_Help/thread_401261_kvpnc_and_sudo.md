---
title: "kvpnc and sudo"
date: 2007-04-04
forum: General Help
---

### Post by Astarus on 2007-04-04
I'm trying to set up a few laptops running xubuntu (Dapper) for checkout at the library where I work. In order to access the internet the patron has to login to a vpn. I have installed kvpnc and it connects fine. My issue is that for kvpnc to connect it has to be run as root (sudo kvpnc). I don't want to have to enter the root password for every patron when they want to use the internet nor would I want to give them the root password. 

I'm kinda new at this but I figure maybe there is a way to change permissions for kvpnc or would it be possible to create a script that launches kvpnc as root but also enters the password "behind the scenes" without the user knowing.

Any ideas?

---

### Post by anywebloco on 2007-06-20
I'd like to know how to do this too. The instructions on the kvpn website don't work for me.

---

### Post by ashz on 2007-06-20
[http://home.gna.org/kvpnc/en/documentation.html]("http://home.gna.org/kvpnc/en/documentation.html")

Howto setup KVpnc for use without root password - sudo

   1. install sudo

   2. edit /etc/sudoers: add an command alias
      # Cmnd alias specification
      Cmnd_Alias KVPNC = /usr/bin/kvpnc

      # User privilege specification
      ALL ALL=NOPASSWD:KVPNC
      adjust the path to kvpnc
         1. SuSE: /opt/kde3/bin/kvpnc
         2. Debian, Fedora, Ubuntu: /usr/bin/kvpnc

   3. edit desktop link:adjust the path to kvpnc
          * SuSE: /opt/kde3/share/applnk/Internet/kvpnc.desktop
          * Debian, Fedora, Ubuntu: /usr/share/applnk/Internet/kvpnc.desktop

      replace the following lines:
      Exec=kvpnc
      X-KDE-SubstituteUID=true
      with:
      Exec=sudo kvpnc
      X-KDE-SubstituteUID=false

---

### Post by anywebloco on 2007-06-21
ashz - did the instructions from the kvpnc website work for you or are you just posting them? They didn't work for me... :-(

---

### Post by Maxtorm on 2007-07-13
Seems this thread is dormant, but I'm going to poke around with this as well.  I suspect part of the problem is that kvpnc depends on vpnc and vpnc depends on having root access.  The first Google hit on sudoers ([http://www.gratisoft.us/sudo/sample.sudoers](http://www.gratisoft.us/sudo/sample.sudoers)) indicates that we can specify commands to run without prompting for the su/root password.  Perhaps if we add vpnc to the list of password-less commands in the sudoers file it will fix the problem?

---

### Post by ScottScottScott on 2008-04-02
I'm using Suse Linux but having the same problem. Note, the recommended method for modifying /etc/sudoers is to use the program visudo which requires vi. Here's how we fixed it:

1) When you use sudo, by default your environment variables changes. You need to have ACCESS or XAUTHORITY in the allowed list of variables. In the file /etc/sudoers You can either comment out the line:
[COLOR="Red"]Defaults        env_keep = "LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS XDG_SESSION_COOKIE"[/COLOR]
or you can modify it to read like this:
[COLOR="Red"]Defaults        env_keep = "LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS XDG_SESSION_COOKIE DISPLAY XAUTHORITY"[/COLOR]

2) In /etc/sudoers there is a note which says "[COLOR="Red"]When configuring sudo, delete the two following lines:[/COLOR]". I missed that when I first setup sudoers so other people may have too. The lines to delete (I just commented them out by prepending with a "#") are:
[COLOR="Red"]#Defaults targetpw   # ask for the password of the target user i.e. root
#ALL ALL=(ALL) ALL   # WARNING! Only use this together with 'Defaults targetpw'![/COLOR]

3) Suse has a graphical utility called Yast (some people hate it, I happen to like it) for system configuration which allows you to choose the user, runas, nopassword and command. It then modifies the /etc/sudoers file. Using yast, the change to sudoers looks like this:
[COLOR="Red"]VPNUser ALL = (root) NOPASSWD: /opt/kde3/bin/kvpnc[/COLOR]
NOTE: I BELIEVE THE PATH TO KVPNC WILL BE DIFFERENT IN UBUNTU!

4) By default, X is not permitting other processes to contact it, you need to turn it off by running "xhost +". I created a desktop icon with the following command to do this then run sudo kvpnc.
[COLOR="Red"]xhost + && sudo /opt/kde3/bin/kvpnc && xhost -[/COLOR]
AGAIN, THE PATH TO KVPNC IS DIFFERENT IN UBUNTU!

As much as I'd like to, I can't take credit for finding this, it was my boss who figured it out. He also sent a message to the kvpnc people so they can update their documentation.

A couple more notes:
I tried setting kvpnc to use the Cisco client, it didn't work, I had to use vpnc.
Kvpnc would not work unless I manually added a logon name in the config file (Preferences - Profile - Authenticate - User data). Without a pre-entered name, I kept getting "no logon name".
The MOTD (message of the day) which pops up when a user connects to my VPN does not work with this client. I wouldn't care if this were for me but I'm creating an image which will be used by our end users and our MOTD includes legal mumbo jumbo. I worked around this by putting the legal notice on the desktop wallpaper.

Sorry for the long winded posting, I think that's everything. Good luck!
Scott

---

