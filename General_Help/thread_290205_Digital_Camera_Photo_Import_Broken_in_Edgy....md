---
title: "Digital Camera Photo Import Broken in Edgy..."
date: 2006-10-31
forum: General Help
---

### Post by johnnymac on 2006-10-31
Hey all..

Just trying to poll around and see if someone else is having the same issue and if so - has anyone got a fix?  I have a workaround but it sux.

Let me break it down for you...

I have an HP Photosmart M425 Digital Camera.  When I plug the camera in things run like they are supposed to until I import the photos.  I get an error due to permissions issue.  I did some digging and found this bug with launchpad...

[https://launchpad.net/distros/ubuntu/+source/gphoto2/+bug/6602](https://launchpad.net/distros/ubuntu/+source/gphoto2/+bug/6602)

There seems to be something horky in the udev rules or something that's preventing and it's around that check_ptp_camera script that was in Dapper.

Anyway - if someone stumbles across this and wants to know how to fix it...

1.  Modify /etc/udev/rules.d/45-libgphoto2 to look like what is in this link:  [http://librarian.launchpad.net/4934174/45-libgphoto2.rules](http://librarian.launchpad.net/4934174/45-libgphoto2.rules)

2.  Add the following check_ptp_camer script to /lib/udev (make it executable):  [http://librarian.launchpad.net/4933902/check_ptp_camera](http://librarian.launchpad.net/4933902/check_ptp_camera)

If you do that - the problem should go away.  This is a hack|workaround but it works.

---

### Post by Ann667 on 2006-11-04
I have the same camera and am having the same problem.

Thanks for the info Johnnymac.

---

### Post by Ann667 on 2006-11-04
I've followed your directions with one little snag... I don't know how to make the check_ptp_camera file executable...  I'm sure it's simple from the command line, but I can't seem to find what command I need to use.  I've searched the forums and my questionably trusty Linux book with no luck.  I created the file with gedit, but don't have permissions to change it to an executable file from the GUI.


Got it!  chmod.  I knew it was simple.

---

### Post by LTBookman on 2006-11-07
> **johnnymac said:**
> Anyway - if someone stumbles across this and wants to know how to fix it...

Thank you, that worked for me! Till now, I was getting round the permission problem by sudo gnome-volume-manager-gthumb %h

---

### Post by spotslayer on 2006-11-07
I did this and it worked up to the point that my  camera will mount and show on the desktop. I can open the picture folder from there and get to the pictures. When the popup comes up and asks what I would like to do and I say open in digikam(using kubuntu) I get the following. 

Failed to list files in /camera

I also get this if I open digikam and try and import from the camera. It would be nice if I could just import directly from the camera into digikam.

David

---

### Post by johnnymac on 2006-11-07
I'm glad I could help some.  Sad to say though...I've moved my production system back to Dapper and have a "testing" system running edgy.  I was running into too many things that seemed unstable and broken.

Sorry though...I'm not much help with the KDE issue though - I'm not a KDE user.  Actually I use Picasa once I get the images off anyway...most of my images go right up on my website.

Hopefully the LTS version of Edgy (whatever that may be) will have these fixed...

---

### Post by Drakkor on 2006-11-30
I am having problems with:
> 2. Add the following check_ptp_camer script to /lib/udev (make it executable): [http://librarian.launchpad.net/4933902/check_ptp_camera](http://librarian.launchpad.net/4933902/check_ptp_camera)

Please enlighten me !  ](*,)

---

### Post by Culito on 2006-12-02
Sigh.  My Kodak CX4230 won't import pics in Edgy.  And I don't think it's PTP compatible...at least there's no option in the camera menu.  What the heck?

Oh, and it's:

sudo chmod +x check_ptp_camera

right?

---

### Post by mkoyle on 2007-01-23
> **Drakkor said:**
> I am having problems with:

2. Add the following check_ptp_camer script to /lib/udev (make it executable): [http://librarian.launchpad.net/4933902/check_ptp_camera](http://librarian.launchpad.net/4933902/check_ptp_camera)

Please enlighten me !  ](*,)

1. Create the file and add the content he said to by opening a terminal (Applications-->Accessories-->Terminal):

sudo gedit /lib/udev/check_ptp_camera

2. Next we want to change permissions (using a file called chmod) to make it executable.  Before we do that, let's take a look at the permissions already there:

ls -l /lib/udev

You will see that your new file has different rwx permissions next to it.  It looks a bit cryptic, but it is really quite easy: the first three are the owner, the next three are the group, and the last three is for everyone else.  Go look for 'chmod how to' on google and you will find a better explanation.  [http://catcode.com/teachmod/](http://catcode.com/teachmod/) explains it rather well.

So now let's do the permission change:

sudo chmod 755 /lib/udev/check_ptp_camera

If you type 

ls -l /lib/udev

you will see that your file is like the others in the directory now.  Hope this helps.

--Matthew

---

### Post by tlindner on 2007-02-21
wow...     good workaround.  This had me stumped for an hour.

---

### Post by AstarothCY on 2007-03-10
Works great, thanks!

---

### Post by DarkStarAeon on 2007-03-19
johnnymac and mkoyle, I could hug you two right now. lol 

THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :grin:

---

### Post by Drakkor on 2007-03-19
Got mine fixed by using rko618's fix here in this thread :
[http://www.ubuntuforums.org/showthread.php?t=381702](http://www.ubuntuforums.org/showthread.php?t=381702)
with this:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

:)

---

