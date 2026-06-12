---
title: "Gnome &quot;Failed to Initialize Hal&quot; error due to NIS"
date: 2005-08-18
forum: General Help
---

### Post by reedlaw on 2005-08-18
I am at my wit's end with this Gnome error.  I posted [here](http://ubuntuforums.org/showthread.php?t=57409&highlight=nis+initialize+hal)  about my problem, but now I have narrowed it down to NIS.  I can run NIS on my client without the error, but if I start NIS on the NIS server I always get the "Failed to Initialize Hal" error.  I followed [this](https://wiki.ubuntu.com/SettingUpNISHowTo) wiki howto when I set up the server and client.
I have tried everything I can think of, even running OpenLDAP instead of NIS but I found that was much more difficult.  I would really like to get NIS running without this error.
Here are my relevant files:
Server:
/etc/yp.conf
```
# ypserver ypserver.network.com

domain ftf server ftf-server
``` 
/etc/ypserv.securenets
```
# Always allow access for localhost
255.0.0.0       127.0.0.0

#255.255.255.0  218.198.178.0
host   218.198.178.227
``` 

/etc/ypserv.conf --unmodified

/etc/defaultdomain
```
ftf
``` 

/etc/hosts.allow
```
portmap ypserv ypbind mountd nfsd statd lockd : 218.198.178.
``` 

/etc/default/nis
```
# Are we a NIS server and if so what kind (values: false, slave, master)
NISSERVER=master

# Are we a NIS client (i.e. start ypbind?)
NISCLIENT=true
``` 

Client:
/etc/default/nis
```
# Are we a NIS server and if so what kind (values: false, slave, master)
NISSERVER=false

# Are we a NIS client (i.e. start ypbind?)
NISCLIENT=true
``` 

/etc/hosts.allow
```
portmap : 218.198.178.138
``` 

/etc/yp.conf --same as above

/etc/passwd
/etc/group
/etc/shadow 
all have the extra lines added to the bottom

This NIS server/client setup works find, including ypcat passwd and client login.  It's just the nasty Hal error that I need to get rid of. 
Any help is greatly appreciated.

---

### Post by reedlaw on 2005-08-19
I have narrowed it down even more now.  If I apt-get remove nis and then restart my client machine, I can get it running without the HAL error.  Then I can reinstall nis and use my client normally, even logging out and changing users.  But as soon as I restart the next time, the HAL error returns.  Could this have to do with something in the boot order?  Should ypbind come after HAL?  I am getting really frustrated here and I would greatly appreciate any suggestions.

---

### Post by reedlaw on 2005-08-22
I'm still working on this problem, and in case anyone is following, I will keep it up to date (until I solve it I hope).
I now know that I can reboot and log in with a normal user and not get the problem.  It begins, however, as soon as I log in with an administrator account.  If I log in with admin, I get "Failed to Initialize HAL", and when I log out and change users, I get the error again, and on and on until I uninstall nis and reboot.
What could it be about an administrator account that could cause this?  My administrator account is a member of the following groups:
admin, scanner, lpadmin, cdrom, floppy, audio, video, plugdev, dialout, dip, adm
Regular users are members of:
lpadmin, cdrom, floppy, audio, video, plugdev
If it is the admin group that's causing it then it's a big proble.  I can remove scanner and dialout.  Does anyone know what dip and adm are for?

---

### Post by KrustybRuffle on 2005-08-22
I get this error when using a newly built kernel, but I do not have nis installed.?

I am just beginning to try to figure this out, but I will post here if I find anything...

---

### Post by reedlaw on 2005-09-14
Problem is fixed in Breezy  \\:D/

---

### Post by Ranime on 2005-10-07
In the words of a famous Vulcan: "Interesting..."

Is it save yet to upgrade to breazy (colony 5)?

---

### Post by cakewalk on 2005-10-09
Thanks reedlaw for tracking this down to NIS. I mannaged to fix it for myself I dont know if this will work for everyone else.

On your nis server edit the /var/yp/Makefile
Find GID_MIN=(some number)
and change it to 1000
save and type make as root
$> sudo make
then restart NIS
$> sudo /etc/init.d/nis restart
should now work

This will stop the HAL group from being replicated by NIS which seems to be the problem. Side effects are ofcourse that none of the system groups will be replicated like audio etc -- which is a pain 
You could try changing the HAL gid/uid lower than the useful groups you would want to replicate ie < 20 but I dont know if that would work??
Everything has been working perfectly for 4 days now -- no more "failed to initialize Hal" :)

---

