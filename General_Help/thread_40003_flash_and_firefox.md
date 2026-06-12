---
title: "flash and firefox"
date: 2005-06-07
forum: General Help
---

### Post by tronica on 2005-06-07
i installed the flash pluging for firefox and now when i visit a site that uses flash, firefox just kills itself, no error messege. I've installed this plugin on other machines and had no problem. does anyone have any suggestions? 

Thanks
Tronica

---

### Post by nemin on 2005-06-07
[QUOTE=tronica]i installed the flash pluging for firefox and now when i visit a site that uses flash, firefox just kills itself, no error messege. I've installed this plugin on other machines and had no problem. does anyone have any suggestions? 
[/QUOTE]Maybe you'll get an error message when you run firefox from the commandline (`mozilla-firefox`) and visit a flash-site?

---

### Post by tronica on 2005-06-07
ok i ran if from the terminal and heres what i get, i just went to nvidia.com and it crashes.

root@ubuntu:/home/lyle # firefox
*** loading the extensions datasource
*** loading the extensions datasource
NP_Initialize
New
SetWindow
Segmentation fault
root@ubuntu:/home/lyle #

---

### Post by hammett111 on 2005-06-07
I can help you here buddy. You are running an AMD64 system like me, and the flash plugins are all 32bit (Macromedia are dragging their knuckles over development). I take it you installed the 64 bit version of Ubuntu/Kubuntu, if so then the Firefox webbrowser is a 64 bit compilation as well, which means the 32 bit flash will not work and will randomly crash your machine on sites that use flash.

Thus you have two options:

1. Remove the flash plugin, and use your browser without it, and wait for flash 64 to arrive (I suggest you join the blogs to convince macromedia to hurry up!!)

2. Uninstall the 64 bit version of Firefox and install via synaptic/kynaptic the 32bit version and then install the flash plugin.

Hope this helps you my man

---

### Post by tronica on 2005-06-07
This does put alot of light on the subject thank you very much, it all makes sense now. I will try it later. 

Thanks

tronica

---

### Post by pix0r on 2005-06-09
I'm on intel 32bit, and I'm having the same problem -- flash pages are crashing firefox.  It'll actually just become unresponsive if I go to a site, and I'll have to kill it.  It doesn't give any output at all, no error messages or anything on stdout or stderr.  I've tried using the binaries off mozilla.org with the same results as the ubuntu ones.

Any other ideas for what could be causing this?

Thanks
Mike

---

### Post by pix0r on 2005-06-09
[QUOTE=pix0r]I'm on intel 32bit, and I'm having the same problem -- flash pages are crashing firefox.  It'll actually just become unresponsive if I go to a site, and I'll have to kill it.  It doesn't give any output at all, no error messages or anything on stdout or stderr.  I've tried using the binaries off mozilla.org with the same results as the ubuntu ones.[/QUOTE]
Ok I think I solved my problem.  I had followed the instructions on ubuntuguide.org to set up ALSA sound, and it involved the command `ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1` .. strace of firefox showed that one of the last syscalls was to load libesd.so.1, so I tried removing the link and voila, flash is working again.

---

### Post by moisty70 on 2005-06-14
That symbolic link didnt worked for me, the error:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 103 error_code 8 request_code 147 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


when executing from console

---

