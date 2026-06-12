---
title: "Permissions - Help Please!"
date: 2008-04-08
forum: General Help
---

### Post by JemW on 2008-04-08
I've created a directory under /usr called '/usr/java'

I want to copy the downloaded JRE rpm.bin file there to install JRE as per the instructions on the java.com site. However, Ubuntu is telling me I don't write permissions for that folder. Can someone tell me how to overcome this please. I crested a root password but this hasn't helped.

Thanks

---

### Post by oldos2er on 2008-04-08
"sudo cp /filename /destination/filename"

 Why are you installing an *rpm? Java is in the repositories.

---

### Post by JemW on 2008-04-08
> **oldos2er said:**
> "sudo cp /filename /destination/filename"

 Why are you installing an *rpm? Java is in the repositories.

I can't find it!??

---

### Post by oldos2er on 2008-04-08
Go to System, Administration, Software Sources, and make sure all repositories are enabled. Then type "sudo aptitude update && sudo aptitude install  sun-java6-jre" in a terminal.

---

### Post by JemW on 2008-04-08
> **oldos2er said:**
> Go to System, Administration, Software Sources, and make sure all repositories are enabled. Then type "sudo aptitude update && sudo aptitude install  sun-java6-jre" in a terminal.

Thanks it's installed, but nothing works: Verify Java or Test Java pages...

---

### Post by jimbob on 2008-04-08
I haven't installed java at all on the last couple of releases I am using and never have I had a problem with anything I have run complaining that it is not there.

Admittedly I dont use much of the computer, just email, web browsing and some openoffice stuff but can someone give me a short list of applications that absolutely must have java to work?

Will the java that is included with Ubuntu handle all java applications?

---

### Post by oldos2er on 2008-04-08
You might need to install java-common and sun-java6-bin as well. I don't know for certain, because I always just install ubuntu-restricted-extras, which takes care of all that stuff.

---

### Post by arvevans on 2008-04-08
To answer your original question:

[INDENT]
Open a terminal screen and type "man chmod".

Use arrow keys to scroll up/down in the man page, and 'esc' key to exit.

Exit that man page and then type "man chown"

[/INDENT]

This will show you how to totally control file and directory permissions in Linux.


Arv
_._

---

### Post by JemW on 2008-04-08
> **arvevans said:**
> To answer your original question:

[INDENT]
Open a terminal screen and type "man chmod".

Use arrow keys to scroll up/down in the man page, and 'esc' key to exit.

Exit that man page and then type "man chown"

[/INDENT]

This will show you how to totally control file and directory permissions in Linux.


Arv
_._

Oh dear. I'm now completely confused.

All I ever wanted to do was install Java for Firefox. As you know, in Windows, that involves installing the current JRE from java.com. Being Linux that page points yoy at the manual downloads which is where this all started - I wanted to install what java.com was telling me I should.

1) When I first visited that page Firefox prompted me automatically to install two things - the manual download I described above, and something called Iced Tea Java Policy Tool, which installed automatically, but does nothing. I've tried to get rid of that but can't see how to. It doesn't seem to be listed anywhere.

2) Since then, Ann gave me this command : **sudo aptitude update && sudo aptitude install sun-java6-jre ** which certainly installed something but hasn't helped Firefox display any Java verification tests, so clearly that wasn't what I needed.

I appreciate all the help but I'm still stuck:

1) How can I get rid of the things I've mistakenly installed that I don't need.

2) What do I then do, by whatever means, to install Java so that my browser (any browser) will work with Java applets.

Many Thanks.

---

### Post by JemW on 2008-04-08
> **JemW said:**
> Oh dear. I'm now completely confused.

All I ever wanted to do was install Java for Firefox. As you know, in Windows, that involves installing the current JRE from java.com. Being Linux that page points yoy at the manual downloads which is where this all started - I wanted to install what java.com was telling me I should.

1) When I first visited that page Firefox prompted me automatically to install two things - the manual download I described above, and something called Iced Tea Java Policy Tool, which installed automatically, but does nothing. I've tried to get rid of that but can't see how to. It doesn't seem to be listed anywhere.

2) Since then, Ann gave me this command : **sudo aptitude update && sudo aptitude install sun-java6-jre ** which certainly installed something but hasn't helped Firefox display any Java verification tests, so clearly that wasn't what I needed.

I appreciate all the help but I'm still stuck:

1) How can I get rid of the things I've mistakenly installed that I don't need.

2) What do I then do, by whatever means, to install Java so that my browser (any browser) will work with Java applets.

Many Thanks.

No-one? My questions might seem basic but all I want to know is how to install the genuine, up to date Flash and Java plug-ins in Firefox. Coming from a Windows background I can't quite understand why it seems to be so hard. However, I'm aware that it is easier with other Linux distros - at least that's what I've been told.

I'm surprised about this because Ubuntu is talked about as the easiest distro for Windows users to get used to. Well, not for me so far...

If someone can take the time to explain to me how I can do what I want then great...

---

