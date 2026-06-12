---
title: "help with bash scripting"
date: 2007-11-26
forum: General Help
---

### Post by eldragon on 2007-11-26
im trying to work a simple script to check from an online source a host file, and append any differences to my local host file..

so far:
i download the hosts file with wget
i do a diff newhostfile /etc/hosts

i receive a list, from which i want to append only the new entries in newhostfile to /etc/hosts

how can this be done?

thanks

this is a great ad blocker. pages load a lot faster.

another failsafe i would like to add (if its simple) is to check that added host entries point to 127.0.0.1 and not somewhere else.

ive got no idea how to process the stream, i was thinking on making a small c program, but i bet theres a simple method already available through scripting.

---

### Post by eldragon on 2007-11-28
bump?

---

### Post by skymera on 2007-11-28
wheww why download a host list?

mine looks like this ```

scott@scott-desktop:~$ cat /etc/hosts
127.0.0.1 localhost scott-desktop
127.0.1.1 scott-desktop

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
scott@scott-desktop:~$ 

```

---

### Post by Swooter on 2007-11-28
Yup, I wrote a simple bash script to download and check for additions to the host file found at: 

[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

If additions were found I updated my "/etc/hosts" file.  

I run the script as a cron job weekly.  I've been doing this for years now...

Let me know if you still need the script.

---

### Post by eldragon on 2007-11-29
> **skymera]
wheww why download a host list?

mine looks like this
[/quote]

well, if you do this, most off site ads are blocked, and your pages just dont load those anoying moving ads on most webpages. gives extra security, reduces bandwidth use, and of course, turns your websurfing almost ad free
you could even set up an apache server and make it load whatever you deem apropiate :)


[QUOTE=Swooter said:**
> Yup, I wrote a simple bash script to download and check for additions to the host file found at: 

[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

If additions were found I updated my "/etc/hosts" file.  

I run the script as a cron job weekly.  I've been doing this for years now...

Let me know if you still need the script.


i would like this script, im having trouble parsing the lines of the downloaded host file, and i dont have much time to learn how sed works...


thanks

---

### Post by Swooter on 2007-11-29
Attached is the bash program I wrote to do just this.

Note that it does require some user modifications (clearly noted at the top of the script).

You can put it where ever you want but it must be executed by root (to be able to edit the /etc/hosts file).  The file should be renamed just "dnldHosts" (or the script modified to dnldHosts.txt) due to upload limitations.

The wget part is done by a non-root user so it is safer. 

I should note that every time it does an update to the /etc/hosts file it creates a copy of the last used /etc/hosts file called "/etc/hosts.old".

Let me know if you have any questions about it.

---

### Post by eldragon on 2007-11-29
thanks for the reply. the script seems alright..

i'll have to work out some differences with what im looking for..

instead of replacing the entire hosts file, i was thinking on doing a diff, and appending just the new stuff only, this way, i could timestamp the changes ;) and add some hosts on my own that dont get removed on every update.

another thing is i was thinking of adding an extra layer of security and checking host ips pointing to 127.0.0.1, so that im not at the mercy of some webmaster's security (think of it as if, someone hijacks the page you get your hostfile...they could do a terrible mess..

i'll make the changes when i get some time, and post here...

cheers..

PS. i still cannot make out how to use sed :(

---

### Post by Swooter on 2007-11-30
Mine won't replace the entire hosts file.  I still keep my customizations...everything you set-up will stay that way.  Only the hosts info added after "START OF.." is appended each time there is an update.

The rest remains the same.

---

