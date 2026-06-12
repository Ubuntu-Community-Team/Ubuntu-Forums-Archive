---
title: "Xsane work only as root"
date: 2005-09-25
forum: General Help
---

### Post by indypende on 2005-09-25
Xsane work only as root. When i use xsane as normal user i get "no scanner" found. Looking on google i see it's a problem of permission of the device. Then i do:

sudo sane-find-scanner

my scanner was correctly found and is on /proc/bus/usb/001/002
Then i do:

sudo chmod a+rw /proc/bus/usb/001/002

Now xsane work correctly also as normal user, but (and this is the problem) at every reboot i loose the permission "rw" on /proc/bus/usb/001/002.

What's the easyest way to do that at every boot?

thanks to all!

---

### Post by papangul on 2005-09-25
Got this by googling:
> Open up /etc/udev/permissions.d/50-udev.permissions in your fav. editor (*cough* vim *cough*) and look for the device that corresponds to your scanner. Make it owned by the group users and give it 0660 permissions. The entry will look roughly like this:

usb/scannerdevicehere*:root:users:0660

Where did you find your method of changing permissions in /proc? That is a virtual filesystem and is created by kernel to list processes, so changes made there are are temporary.

---

### Post by indypende on 2005-09-25
This is my /etc/udev/permissions.d/udev.permissions but i can't find no device like my scanner? any suggestion?
# name:user:group:mode

# character devices

ptmx:root:tty:0666
random:root:root:0666
urandom:root:root:0444
kmem:root:kmem:0640
mem:root:kmem:0640
port:root:kmem:0640
null:root:root:0666
zero:root:root:0666
full:root:root:0666

misc/nvram:root:nvram:660
nvram:root:nvram:660
misc/rtc:root:audio:0664
rtc:root:audio:0664
inotify:root:root:0666

tts/*:root:dialout:0660
bluetooth/rfcomm/*:root:dialout:0660
tty[BCDEFHILMPRSTUVWX][0-9]*:root:dialout:0660
ttyS[ACIR][0-9]*:root:dialout:0660
ttyUSB[0-9]*:root:dialout:0660
ttyACM[0-9]*:root:dialout:0660
ippp[0-9]*:root:dialout:0660
isdn[0-9]*:root:dialout:0660
isdnctrl[0-9]*:root:dialout:0660
capi[0-9.]*:root:dialout:0660
dcbri[0-9]*:root:dialout:0660
ircomm[0-9]*:root:dialout:0660
rfcomm[0-9]*:root:dialout:0660
tty:root:tty:0666

snd/*:root:audio:0660
sound/*:root:audio:0660
admmidi*:root:audio:0660
adsp*:root:audio:0660
aload*:root:audio:0660
amidi*:root:audio:0660
amixer*:root:audio:0660
audio*:root:audio:0660
dmfm*:root:audio:0660
dsp*:root:audio:0660
audio*:root:audio:0660
mixer*:root:audio:0660
music:root:audio:0660
sequencer*:root:audio:0660

printers/*:root:lp:0660
usb/lp[0-9]*:root:lp:0660
usb/legousbtower[0-9]*:root:root:666
lp[0-9]*:root:lp:0660
parport[0-9]*:root:lp:0660
irlpt[0-9]*:root:lp:0660
usblp[0-9]*:root:lp:0660

input/mice:root:root:0600
input/mouse[0-9]*:root:root:0600
input/js[0-9]*:root:root:0644
input/*:root:root:0600
mouse[0-9]*:root:root:0600
js[0-9]*:root:root:0644
sonypi:root:root:0666

dri/card[0-9]*:root:video:0660
fb/*:root:video:0660
fb[0-9]*:root:video:0660
agpgart:root:video:0660
nvidia*:root:video:0660

v4l/*:root:video:0660
video[0-9]*:root:video:0660
radio[0-9]*:root:video:0660
vbi[0-9]*:root:video:0660
vtx[0-9]*:root:video:0660
dvb/*:root:video:0660

raw1394:root:video:0600
# When the kernel gets proper support for 1394, change this to a wildcard:
video1394/0:root:video:0660

# block devices

floppy/*:root:floppy:0660
fd[0-9]*:root:floppy:0660
cdemu/*:root:cdrom:0660
pktcdvd/*:root:cdrom:0660
pktcdvd/control:root:root:0644

ram[0-9]*:root:disk:0660
raw/*:root:disk:0660

ide/*/cd:root:cdrom:0660
ide/*:root:disk:0660
hd[a-s]:root:disk:0660
hd[a-s][0-9]*:root:disk:0660

scsi/*/cd:root:cdrom:0660
scsi/*:root:disk:0660
sd[a-z]:root:disk:0660
sd[a-z][0-9]*:root:disk:0660
sd[a-i][a-z]:root:disk:0660
sd[a-i][a-z][0-9]*:root:disk:0660
s[gr][0-9]*:root:disk:0660
scd[0-9]*:root:cdrom:0660

dasd[0-9]*:root:disk:0660
ataraid[0-9]*:root:disk:0660

loop/*:root:disk:0660
loop[0-9]*:root:disk:0660
md/*:root:disk:0660
md[0-9]*:root:disk:0660
dm-*:root:disk:0640

ht[0-9]*:root:tape:0660
nht[0-9]*:root:tape:0660
pt[0-9]*:root:tape:0660
npt[0-9]*:root:tape:0660
st[0-9]*:root:tape:0660
nst[0-9]*:root:tape:0660

sgi_fetchop:root:root:666
iseries/vcd*:root:disk:660
iseries/vd*:root:disk:660

---

### Post by papangul on 2005-09-25
Now it's beyond me, but you can experiment with this :guesswork only:
```
usb/legousbtower[0-9]*:root:root:666
```

---

### Post by Zalbor on 2005-09-25
Did you try System>Administration>Users and Groups>(click on user)>Properties>User privileges>Use scanner devices?

---

### Post by indypende on 2005-09-26
*Now it's beyond me, but you can experiment with this :guesswork only:
*Code:
*
*usb/legousbtower[0-9]*:root:root:666

Not working.

*Did you try System>Administration>Users and Groups>(click on *user)>Properties>User privileges>Use scanner devices?

Thanks for the suggestion but this is the first control that i made. "Use scanner devices" is enabled for the normal user (also by default!)

I've discovered that's a bug: #16232 

we can continue try to solve the problem in bugzilla. Thanks again!

---

### Post by kleeman on 2005-09-26
And also bug #12496    	(that's mine thar kiddo!) Duplicate?

---

### Post by kleeman on 2005-09-27
Works now perfectly for me with reverted hotplug setup which is the upshot of the bugzilla discussion on bug number 16232 (package updated 9/27). Because I had run xsane as root I found I needed to delete manually my .sane directory as there were a bunch of root owned files in there. Three cheers for the developers!

---

### Post by indypende on 2005-09-28
[QUOTE=kleeman]Works now perfectly for me with reverted hotplug setup which is the upshot of the bugzilla discussion on bug number 16232 (package updated 9/27). Because I had run xsane as root I found I needed to delete manually my .sane directory as there were a bunch of root owned files in there. Three cheers for the developers![/QUOTE]
Not working for me!
what have you do?
:???:

---

### Post by kleeman on 2005-09-28
I just updated using 

sudo apt-get update && sudo apt-get dist-upgrade

That bug is still open by the way if you want to interact with a developer....

---

### Post by PhilOSparta on 2005-10-04
[QUOTE=indypende]*you can experiment with this :guesswork only:
*Code:
*
*usb/legousbtower[0-9]*:root:root:666
[/QUOTE]
I started having this problem today and changed the above line in 
/etc/udev/permissions.d/udev.permissions  to
usb/legousbtower[0-9]*:users:users:666   
I rebooted and the scanner was detected, but why would this problem start when breezy has been working all along?  Also, on exiting Xsane, several files were unable to be written.   
I changed the files in the .sane directory to have me as the owner using chown phil * thus eliminating the values that were set while running the program as root. (i.e. sudo).
Now everything works for all users.

---

### Post by zalun on 2005-10-05
I think the better way is to use network scanning:
Here is how to do it - [http://penguin-breeder.org/sane/saned/]("http://penguin-breeder.org/sane/saned/")
If you will have simillar problem as I wrote here - [http://ubuntuforums.org/showthread.php?t=72055&highlight=xsane]("http://ubuntuforums.org/showthread.php?t=72055&highlight=xsane")
please leave me a note.

thank you

---

