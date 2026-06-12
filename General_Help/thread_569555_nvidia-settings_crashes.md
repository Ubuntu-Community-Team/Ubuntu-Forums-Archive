---
title: "nvidia-settings crashes"
date: 2007-10-07
forum: General Help
---

### Post by Placified on 2007-10-07
hello,
     I'm new to linux and I have encountered a problem with my nvidia settings.  I installed the latest drivers from nvidia and set up my two monitors and one tv all are working fine, but when I run sudo nvidia-settings and go to glx/opengl information the app crashes.  The terminal puts out this message

The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 276 error_code 3 request_code 144 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

this didnt start happening till after I updated my xorg with the nvidia control panel to enable my extra displays to work with xenerama I'm fairly sure that whatever has happened has killed my opengl.  I have looked around and cant find another instance of this problem any help would be apreciated.  if you need clarification or more information just ask I'll be checking this post often.  

Thanks in advance

---

