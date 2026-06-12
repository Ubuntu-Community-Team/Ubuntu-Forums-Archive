---
title: "Cant get OIDENTD working tried everything .. HELP!!"
date: 2007-02-10
forum: General Help
---

### Post by akz on 2007-02-10
Im currently got a Kubuntu 6.10 (Edgy) box running and using it to tunnel ipv6 ips via a tunnel brooker. (the ipv4 > ipv6 kind not running any ipv6 tunneling software on the box itself)

Basically I want to be able for the Eggdrops on my box to have the identd/psybnc/irssi have identd working with the specified username in their respective confs.. 

Ive installed Oidentd onto the box.. it started up once but it dosnt work anymore .. here is what I did basically..

logged in as root via sudo -i
- apt-get install oidentd (it finds it and installs it and starts it up)
- I edit oidentd.conf (my current conf looks like below)
```

default {
        default {
                deny spoof
                deny spoof_all
                deny spoof_privport
                allow random_numeric
                allow numeric
                allow hide
        }
}

user root {
        default {
                force reply "UNKNOWN"
        }
}
NOTE:Ive tried setting everything to allow as well but it still does not work.. 

```
-Save it
-/etc/init.d/oidentd stop (stops oidentd)
-/etc/init.d/oidentd start (restart the dameon)

still as root I tried irssi -h custom.vhost.com 
and then /connect -6 irc.az.za
but Im still getting NO IDENTD RESPONSE....

Ive also tried downloading the package and installing it myself but still did not work ... Ive also tried doing the following I found in the ubuntuforums while doing a search..

and i made a ~/.oidentd.conf that got this info

```
global { reply "myidentd" }
```

i edited the /etc/oidentd_masq.conf, added the line
```

192.168.1.x identd UNIX (x is my box's internal ip)

```

still nothing...  does any of you have a tutorial on how to get this up and running sucessfully? 

My box is behind a router (Linksys WRT54G firmware: latest TOMATO) forwarded ports 113 udp/tcp to the machine... 

Thanks for all your replies in advance guys :)

---

### Post by madmonk3y on 2007-06-12
First of all, you will need the allows for spoofing, since you are trying to spoof.  Make your /etc/oidentd.conf this:

```

default {
        default {
                allow spoof
                allow spoof_all
                allow spoof_privport
                allow random_numeric
                allow numeric
                allow hide
        }
}

user root {
        default {
                force reply "UNKNOWN"
        }
}

```

Next, oidentd will run as a non-privledged user (like user nobody and group nobody), so you'll need to make sure that a non-privleged user can get to the ~/.oidentd.conf file.

Make sure that you:

```

sudo chmod a+x /home
sudo chmod a+x /home/(user)

```

Also make sure that you allow the non-privledged user to read the .oidentd.conf file:

```

sudo chmod a+r /home/(user)/.oidentd.conf

```

You will also need to make sure port 113 isn't firewalled.

That should do it.

[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

