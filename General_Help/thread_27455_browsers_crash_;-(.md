---
title: "browsers crash ;-("
date: 2005-04-16
forum: General Help
---

### Post by oldmarti on 2005-04-16
I have a 3 machines all with ubuntu 5.04.
I make all updates. No extra packages. But... firefox crash on all 3! The computer with 
Nvidia Card, linux crash too (I see there is a thread about problem in nvidia driver). 
Firefox crash on Ati Radeon 9600 and Sis 630 too. Maybe this is not bug only v nVidia driver? I test Epiphany browser - the result is same. Only Opera 7.53 work normaly (for now). Any ideas? (this site crash browsers permanently : mobile.bg , but he is not the only one)

---

### Post by erkki70 on 2005-04-16
Hi, 
I guess you should check if the flash plugin is installed, it will avoid crashing your browser.
Good luck and hope this helps.

Cheers,
Erkki

---

### Post by oldmarti on 2005-04-16
flash plugin don't solve the problem, I already try it. I try enable/disable javascrit and java - no difference.

---

### Post by erkki70 on 2005-04-16
Hi,
Could you run Firefox from terminal and post the output to see error messages?

Cheers,
Erkki

---

### Post by oldmarti on 2005-04-16
Here is output in terminal mode:
NP_Initialize
New
SetWindow
SetWindow
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 35 error_code 171 request_code 147 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by oldmarti on 2005-04-16
and here is output, when I start firefox with --sync parameter:
NP_Initialize
New
SetWindow
SetWindow
SetWindow
New
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
DestroyStream
Illegal instruction

---

### Post by erkki70 on 2005-04-16
Can you post your Firefox version?
In case it's 1.01, update should fix the prob as explained in this thread.
[http://www.ubuntuforums.org/showthread.php?t=15726](http://www.ubuntuforums.org/showthread.php?t=15726)

If not some said that Nvidia drivers had something to do with it and using nv drivers solved the prob.

Hope it helps...

---

### Post by oldmarti on 2005-04-16
Funny epiphany produce same results in terminal window ;-)))
Here is the output:
NP_Initialize
New
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
DestroyStream
Destroy
The program 'epiphany' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 35 error_code 171 request_code 147 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by oldmarti on 2005-04-16
Firefox version is 1.0.2. I know a probem with nVidia cards, but now I am on compter with Sis 630. 
       Device          "Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA D$        
(line in my xorg.conf file)

---

### Post by erkki70 on 2005-04-16
Well, looks like it's probably the Nvidia thing...
Someone mentionned using nvidia-glx 6629 drivers and no crash...

---

### Post by oldmarti on 2005-04-16
Try to open this page:
  [http://mobile.bg/](http://mobile.bg/)
After the page is loaded, press on "&#1058;&#1066;&#1056;&#1057;&#1045;&#1053;&#1045;" (this is "search" on english)

---

### Post by erkki70 on 2005-04-16
Yep. Works fine with me.
I don't have this prob at all but I'm now on a laptop with ati card so can't help much or compare I'm afraid...
Definitely the Nvidia problem though.

Good luck.

Cheers,
Erkki

---

### Post by oldmarti on 2005-04-16
But I am not with nvidia video card now!!! Checking with synaptic - no nvidia packages installed, exept nvidia-kernel-common!

---

### Post by Steph on 2005-04-16
When I select File | Import in the Bookmarks Manager, Firefox 1.0.2 immediately crashes - and also crashes Thunderbird, and locks up my profile. 

Apparently this is considered by Mozilla as an [old Firefox bug](https://bugzilla.mozilla.org/show_bug.cgi?id=236607) which has been resolved.

I have no problems with importing bookmarks into Firefox 1.0.2 on other platforms, and I also had no problems when I was running Firefox 0.8.9 on Warty. 

I've searched all over the place and can't even find anyone else reporting the same problem. Can anyone offer any help?

---

### Post by emmeborn on 2005-04-16
I can't help you becouse I have the same problem. I have a ATI Mach 64 video card and no nVidaia drivers installed.
I can not figure out what it is that has happened.
Anyone that has any ideas????????? :-?

---

