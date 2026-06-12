---
title: "unable to open Spotify and Firefox +others"
date: 2022-05-26
forum: General Help
---

### Post by mikber18 on 2022-05-26
Hi Guys, 

I've recently installed ubuntu for the first time in a very very long time. I had a couple of issues along the way during the install but we got there in the end. 

I am however having trouble with certain software (Mozilla Firefox and Spotify) for example. 

I am able to install Spotify ok but it does not open. It becomes unresponsive. I've installed it via the Ubuntu Software centre. 

Likewise, Mozilla Firefox will not open even though it is installed and I can see it on the list of apps. I am having to use Microsoft Edge to access the internet- which incidently I was able to install without a hitch. 

Its very hit and miss. 

I am running Ubuntu 22.04 LTS. 

Please help. 

This is what happens when I try to open Spotify: please see attached screenshot.

Please can you help.
Many Thanks,

---

### Post by mikber18 on 2022-05-26
When I type in firefox into the terminal I get this message: 

> 
Message: 10:35:52.063: Failed to load module "canberra-gtk-module"
Gtk-Message: 10:35:52.064: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.


(firefox:13212): Gdk-WARNING **: 10:35:52.658: The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc'.
  (Details: serial 540 error_code 11 request_code 146 (unknown) minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Exiting due to channel error.


---

### Post by &amp;KyT$0P# on 2022-05-26
Regarding Firefox, does the problem still occur if you use the [latest official Mozilla build]("https://www.mozilla.org/firefox/all/#product-desktop-release")?

---

### Post by mikber18 on 2022-05-26
I don't understand. I'm installing the latest build from the snap store - which should be the same as the one on the website? 

Either way it does not run despite multiple tries of Snap remove and snap install etc. Wold you have any other ideas?  I have this issue with multiple apps, Firefox, Discord, Spotify...

---

### Post by &amp;KyT$0P# on 2022-05-26
> **mikber18 said:**
> I don't understand. I'm installing the latest build from the snap store - which should be the same as the one on the website?

I think it's a different build.  Additionally, snaps have additional restrictions and use snap-provided libraries instead of the system libraries.

Are all the apps you're having trouble with installed as snaps?

---

### Post by mikber18 on 2022-05-26
> **halogen2 said:**
> I think it's a different build.  Additionally, snaps have additional restrictions and use snap-provided libraries instead of the system libraries.

Are all the apps you're having trouble with installed as snaps?

Yes. I do believe that to be true. I've just managed to install firefox and it seems to be working fine. It was not through snaps though it was through trial and error. it works now though. 

Its Spotify that is on the hunt list next.....

---

### Post by mikber18 on 2022-05-26
Update. By not using the snaps but instead using flatpacks or trusty apt I was able to install both Spotify and Firefox. The key to my success was to make sure that the snap equivelants of both those apps were properly removed before trying to open the other Firefox or Spotify

---

