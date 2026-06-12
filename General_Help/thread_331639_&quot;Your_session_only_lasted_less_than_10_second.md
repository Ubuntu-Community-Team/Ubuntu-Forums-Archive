---
title: "&quot;Your session only lasted less than 10 seconds&quot;"
date: 2007-01-04
forum: General Help
---

### Post by k4wedi on 2007-01-04
I just booted up Ubuntu today (from dual boot) and this is the error I get when I try to login:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details: (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "po"
/etc/gdm/Xsession: Beginning session setup... "

I searched the forums for similar problems however all the other error messages were different so the solutions and reasons why this happened was different as well.

The last thing I did was try to get bash_profile to run (since for some reason it doesn't..) and I guess I messed up something with xsession...

I have no idea what I'm doing right now so any help would be apperciated. :)

---

### Post by teaker1s on 2007-01-04
I'm guessing you have cocked up your xorg configuration from experience. try 

**sudo dpkg-reconfigure xserver-xorg **

and follow the instructions

---

### Post by scrooge_74 on 2007-01-04
try login in from a terminal and do:  df

check that you have not run out of disk space

---

### Post by k4wedi on 2007-01-04
I tried the **sudo dpkg-reconfigure xserver-xorg ** and still continue to get the same error messages.

Also did the "df" and found that I still have plenty of disk space.

Does anyone else know? :(

---

### Post by bhupeshdogra@gmail.com on 2007-01-05
I am also getting this problem since morning exactly same
i tried login in failsafe mode there it even not found sudo and ls command 
then i login as a root login and i logged in with startx
and i logged in

but dont know how to logg in as my user name

any thoughts over this:rolleyes:

---

### Post by nsabatino on 2007-01-05
I sometimes get the same error with girls.

---

### Post by firecrotch on 2007-01-05
> **nsabatino said:**
> I sometimes get the same error with girls.


HAHAHA! That's a good one! =D>

---

### Post by Falcorian on 2007-01-05
Have you installed any themes recently? I got this error when I installed a bad theme.

If so, try removing it by logging in through the terminal and removing it from ~/.themes

---

### Post by bhupeshdogra@gmail.com on 2007-01-05
> **Falcorian said:**
> Have you installed any themes recently? I got this error when I installed a bad theme.

If so, try removing it by logging in through the terminal and removing it from ~/.themes

i just added variable in my .bashrc file
for oracle 

thats all

---

### Post by ~LoKe on 2007-01-05
How about removing it?

---

### Post by bhupeshdogra@gmail.com on 2007-01-05
> **~LoKe said:**
> How about removing it?

what to remove its bit irritating any soln plzzzzzzzzzzzz
otherwise i have to reformat my system

---

### Post by GrumpyBob on 2007-01-05
Login as failsafe, go to your home folder and delete or rename .ICEauthority (it's a hidden file - has a dot as its first character), then try logging in.  I think the file gets recreated.  Other advice I've seen is to change its ownership:
"sudo chown user /home/user/.ICEauthority" where user = your username.

I had this problem quite some time ago, and this solved it.  

Robert

---

### Post by teaker1s on 2007-01-05
.ICEauthority  I've had that too worth a try

---

### Post by rioghal on 2007-01-05
If the permission/ownership of the .ICEauthority file has changed, it could be due to running a GUI app with sudo instead of gksu or gksudo. That is what happened to me because I didn't know to use gksu or gksudo for GUI apps instead of sudo.

More about this here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by GrumpyBob on 2007-01-06
Amusingly, this happened to me this morning.  Logged in failsafe, renamed .ICEauthority and upon logging in again all was well.  

Robert

---

### Post by iblicf on 2007-01-19
i have met this trouble last night ,, just download some audacious  skin, firefox save it to some tmp ,,i dont mind at that time ,,( it must be /tmp ) , then i want to copy and decompress to audacious directoroy (/usr/share/audacious/Skin ) ,it wont work within my LOGIN_ID ,so i "sodo mv /tmp  " ,,,  i think this command is really stupid !
 
then  looking for the forum ...after done sth that above guys say ,,
it's no use ,, so i just " sudo chmod 777 /tmp" ,,then ...i can login now  ! 

i have deleted the ~/.gnome  .gconf  .gconfd  .ICE*  before

hope this may help sb ..,,

---

