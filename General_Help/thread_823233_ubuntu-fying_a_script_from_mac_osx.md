---
title: "ubuntu-fying a script from mac osx"
date: 2008-06-09
forum: General Help
---

### Post by mm405416 on 2008-06-09
hey all

I've been using ubuntu for a while now, and loving every second of it.  Not too long ago lifehacker made a most called "[Do More with Your Webcam]("http://lifehacker.com/393274/do-more-with-your-webcam-with-free-tools")" 

some of the ideas presented sounded really interesting and worth messing around with.  One such idea that caught me was taking a picture on each invalid login attempt. Now when it comes to something like this, I'm a bit of a newbie, so can anyone explain to me how I could use the provided found [here,]("http://www.macosxhints.com/article.php?story=2006120918170984") or even script my own version of this in ubuntu.

I really hope that someone can give me some direction in this, and I'll try and reciprocate as much as possible.

---

### Post by ryanhaigh on 2008-06-09
I couldn't find the original script but here is a VERY basic script that checks the syslog every 10s for an invalid login message and takes a photo if it is found, from the brief description this is similar to the way the mac script works:


```

#/bin/bash
#checks syslog for gdm login failure and captures photo from webcam

while [ 1 == 1 ]
    do
        #if the quoted text is fount in the file
        if tail /var/log/syslog | grep gdm | grep -q "Couldn't authenticate user"
            #then capture an image (requires xawtv installed)
            then streamer -c /dev/video0 -b 16 -o /home/YOURUSERNAME/outfile.jpeg
        fi
    #wait 10 seconds before looking again
    sleep 10s
    done

```

I would be interested in seeing this improved as its a pretty good idea but I couldn't find any better way to be notified of an invalid login in my brief search, will keep looking though.

EDIT: this would go in /etc/rc.local so it is run at startup, don't forget to change YOURUSERNAME and maybe adjust the time.

---

