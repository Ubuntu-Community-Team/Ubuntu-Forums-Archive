---
title: "Run A Script As SU Without Humand Intervention"
date: 2008-04-02
forum: General Help
---

### Post by kempy1000 on 2008-04-02
Hello,

I am trying to make two scripts excecutable from buttons I have put in my mythtv menu.
The buttons are Stop Azureus and Start Azureus.

I have got two scripts (not my work) which when ran start or stop Azureus in headless console mode in a screen perfectly, no problem there at all.

The problem is trying to run the scripts from mythtv, when I run the scripts as my login it askes for the SU password; as it should becuase the script needs it. 

However I want these scripts to be able to run without having to insert the SU password. 
I cannot remove SU from the scripts, or it functions incorrectly.

I would also like to add im fairly new to linux :) but ill try!

Thanks
Chris

AZ_Start.sh
```


 #! /bin/sh

#Start Headless Azureus

 #The user that will run Azureus
 AZ_USER=azureus

 #Name of the screen-session
 NAME=azureus_screen

 #executable files in the following paths that are perhaps needed by the script
 PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/azureus/bin:/home/azureus/azureus

 #your path to the azureus directory, where Azureus2.jar is located
 DIR=/home/azureus/azureus

 #Description
 DESC="Azureus screen daemon"

    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "Azureus is already running!"
    else
       echo "Starting $DESC: $NAME"
       su $AZ_USER -c "cd $DIR; screen -dmS $NAME java -jar ./Azureus2.jar --ui=console"
    fi

exit 0


```

AZ_Kill.sh
```


 #! /bin/sh

#Kill Headless Azureus

 #The user that will run Azureus
 AZ_USER=azureus

 #Name of the screen-session
 NAME=azureus_screen

 #executable files in the following paths that are perhaps needed by the script
 PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/azureus/bin:/home/azureus/azureus

 #your path to the azureus directory, where Azureus2.jar is located
 DIR=/home/azureus/azureus

 #Description
 DESC="Azureus screen daemon"

    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "Stopping $DESC: $NAME"
       su $AZ_USER -c "screen -X quit"
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi

 exit 0


```

---

### Post by ozymo on 2008-04-02
I'm not sure about running su without human interaction, but you can pass the -S flag to sudo, and it will read the password from standard input, ie:

```
cat /path/to/filename | sudo -S command
```

Obviously, you'll need to replace the pertinent parts.

Please note that this isn't very secure, as it will leave a plaintext password file on your box, but assuming you use appropriate permissions, all should be OK.

I hope this is helpful!

/cs
[~chuck/blog]("http://www.ozymo.com/~chuck/blog")

---

### Post by bodhi.zazen on 2008-04-02
Make both scripts owned by root.root (for security sake)

Then configure sudo to allow you to run those scripts without a password.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)
[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)

---

### Post by kempy1000 on 2008-04-02
> **bodhi.zazen said:**
> Make both scripts owned by root.root (for security sake)

Then configure sudo to allow you to run those scripts without a password.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)
[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)
Hey thanks for the responses.

ozymo I would rather not store my password plain text so i tried bodhi.zazen method. 
Thank you anyway!

I tried what was said and added this to the sudoers file: 

%mythtv ALL = NOPASSWD: /home/mythtv/.mythtv/mythscript/AZ_Kill.sh, /home/mythtv/.mythtv/mythscript/AZ_Start.sh, /usr/bin/sudo

I logged in as mythtv and ran the script and still asks for a password.

But looking at the scripts its saying su $AZ_USER (su azureus) which, if im correct, means im logging in as azureus temporerily doesnt it?

So the password im being asked for is the user "azureus"s

... I Think.....

Thanks
Chris

---

### Post by bodhi.zazen on 2008-04-02
Yes, it is a little more complex. You will need to configure sudo.

If you su to azureus, then yes you will bu entering azureus's password.

What I suggest is to use sudo. If you do not want to run as root, use the -u option.

sudo -u azureus /path/to/script

In that case, with sudo, you would use your log in password. Also, in this case, the script should be owned by azureus.azureus (rather then root).

Once that is configured, you can configure sudo to allow no password.

You may also want to look at expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

