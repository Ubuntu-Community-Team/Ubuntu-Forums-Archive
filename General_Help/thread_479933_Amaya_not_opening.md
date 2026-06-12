---
title: "Amaya not opening"
date: 2007-06-20
forum: General Help
---

### Post by coolglobal on 2007-06-20
Hello guys,

I've just installed **Amaya** using Add/Remove to Feisty.  It won't open when selected from the Application area or any icon.  Anyone know anything about this bug?

Second question:  Anyone using NVU on Feisty - does it go OK.

Waiting with interest...

---

### Post by johnc4510 on 2007-06-20
For Amaya, try launching it in a terminal    gksudo amaya    and then post the output back here.

Also NVU runs fine on feisty    :->

---

### Post by coolglobal on 2007-06-20
Hey John, here's the output: Thanks.


coolglobal1@coolglobal1:~$ gksudo amaya
(amaya:8143): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7085 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
coolglobal1@coolglobal1:~$

---

### Post by wheezer on 2007-06-21
> **johnc4510 said:**
> For Amaya, try launching it in a terminal    gksudo amaya    and then post the output back here.

Also NVU runs fine on feisty    :->

I am having the same problem, almost.  Amaya installed from Synaptic opens for a second, and then closes.

Also, you mention NVU.  I see almost no real development on that since last year. The forum moderators have all moved to a forum site with a whopping 76 users, and it runs so slowly, it might be shared hosting running on a commodore 64.  Do I really want to get into FOSS solution that seems that moribund?  Am I missing something about it?  There is also no speciflc Ubuntu, and it's not clear whether Kompozer is really the better fork.  Can you shed some light on each, and what the future holds for these?  I currently use Aptana, but it has a long way to go for certain levels of basic HTML friendliness.

UPDATE
I installed the latest build from the website, 9.54, and it now opens. 
[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

But John, I still would appreciate any feedback you can offer on NVU/Kompozer

---

### Post by coolglobal on 2007-06-21
Yes, I now seem have a working Amaya, downloaded direct.  There must be something up with Synaptic version?

---

