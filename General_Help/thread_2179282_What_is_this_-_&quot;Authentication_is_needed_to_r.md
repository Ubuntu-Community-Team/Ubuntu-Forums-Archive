---
title: "What is this - &quot;Authentication is needed to run /usr/bin/dropbox as the super user&quot;?"
date: 2013-10-07
forum: General Help
---

### Post by Tom_Carr on 2013-10-07
I have been running drop box for months, and I don't remember ever having this message before.  Why do I have it now?
"Authentication is needed to run /usr/bin/dropbox as the super user"?

---

### Post by ajgreeny on 2013-10-07
When do you see this message and how are you trying to start dropbox?

I suspect most users who run dropbox start it in the autostart list of the session setup, which would mean it is being started as user, not as root, so this is a bit baffling.

---

### Post by Tom_Carr on 2013-10-07
I saw the message when I turned on the computer this morning.
I don't know how dropbox starts.  I set it up months ago and it all works automatically.  I just followed the defaults during setup.

---

### Post by will547_us on 2013-10-16
I got the same message a few minures ago after starting computer. Usually there is a dropbox icon in the tool bar that I would click on to open dropbox, there is not one now?

---

### Post by stevecam on 2013-11-09
Just had the same problem myself, I just looked in my /run/user/1000 directory and saw a file called pulse owned by root
I removed it, and my pulseaudio is now working, maybe this solves the problem for somebody else

---

### Post by thilina on 2013-12-26
This can be fixed by correcting the **PARENT_DIR** variable in the dropbox executable. It points an invalid location. If you need to find a guide on how to fix this, please refer to [http://blog.ishans.info/2013/12/26/fixing-authentication-is-needed-to-run-usrbindropbox-as-the-super-user-error-in-linux/]("http://blog.ishans.info/2013/12/26/fixing-authentication-is-needed-to-run-usrbindropbox-as-the-super-user-error-in-linux/")

---

### Post by gregorydillon on 2014-01-11
add me as another report of this problem.   I'm going through the suggestions here, looking for the solution.

---

### Post by augustin-riedinger on 2014-01-16
thilina's link worked for me. 

But no information about why did this issue occur suddenly, neither in the comments.

That is especially surprising because the result is simply to change
PARENT_DIR = os.path.expanduser("/var/lib/dropbox")
into
PARENT_DIR = os.path.expanduser("~")

So I checked both folders and they both contain the required subfolder .dropbox-dist:
DROPBOXD_PATH = "%s/.dropbox-dist/dropboxd" % PARENT_DIR

Maybe there was an update and it now installs to ~ instead of /var/lib/dropbox earlier. 
But I don't like the idea to have some program installed 2 times on my machine. Especially when one of the two doesn't actually works correctly.

Anyway, explanations will be very appreciated.

---

### Post by severin3 on 2014-01-29
Last step does not work for me: despite I am connected as the (one and only) administrator, the dropbox file is read-only so I cannot neither modify nor delete it. Is there a was to bypas this?

---

### Post by dietmar-5 on 2014-02-08
Thank you [**[COLOR=#000000]thilina[/COLOR]**]("http://ubuntuforums.org/member.php?u=149367") your [help]("http://blog.ishans.info/2013/12/26/fixing-authentication-is-needed-to-run-usrbindropbox-as-the-super-user-error-in-linux/") works fine for me. Dropbox starts as it was before :)

---

### Post by cyncicle on 2014-02-10
> **augustin-riedinger said:**
> thilina's link worked for me. 

But no information about why did this issue occur suddenly, neither in the comments.


Yeah, same here.  Hopefully someone will chime in with an explanation.

---

### Post by kwph on 2014-03-13
What worked for me was to give read permissions to everyone for the /var/lib/dropbox/ directory and files:

sudo chmod -R a+r /var/lib/dropbox/

---

### Post by jmriverofernandez-4 on 2014-04-02
I had the same issue. I followed these steps, and it got solved.
Hope it works.
[http://www.webupd8.org/2014/01/fix-dropbox-fails-to-start-with.html](http://www.webupd8.org/2014/01/fix-dropbox-fails-to-start-with.html)

---

### Post by berthold1 on 2014-05-27
I am having the same problem, and I haven't seen a complete answer to the original question: WHY is this happening now when it did not before? Since I did not do anything to cause the change, a suspicion arises that this might be a phishing attempt. Unless a software update overwrote the precious executable and therefore the permissions were changed? I guess I can change the permission, but I still feel a bit uneasy about this.

---

