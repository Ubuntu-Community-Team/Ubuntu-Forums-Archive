---
title: "Help writing a startup script"
date: 2007-09-10
forum: General Help
---

### Post by gazlang on 2007-09-10
HI,

I have installed an app called cwiid for allowing a wiimote to be used as a mouse.

Once installed, the command 'sudo wminput -w -c iir_ptr' must be run from the terminal to initiate scanning for available wiimotes.

What I need is a start-up script to put into /etc/innit.d, for example, that starts up wminput on reboot and keeps t restarting untill a wiimote is found.
 
 Simply adding wminput -w -c ir_ptr as a cronjob doesn't work because wminput will fail and exit if the bluetooth adaptor hasn't found the wiimote.
 
 I have no clue how to write startup scripts, so does anybody have an idea of how to put something like this together?

Would it be enough to create a file in /etc/innit.d containing the line 'wminput -w -c ir_ptr' to run wminput for one instance?

If so, then how would I get wminput to keep restarting until the wiimote is found?

Thanks in advance

Gareth

---

### Post by s26c.sayan on 2007-09-10
Have a look at this : [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

No guarantees from me!! :D

---

### Post by bodhi.zazen on 2007-09-10
Try just adding 

wminput -w -c iir_ptr

to /etc/rc.local

(Add it to the bottom of the file).

---

### Post by gazlang on 2007-09-10
OK, thanks,

Can I change the 'exit 0' at the bottom of the rc.local page in some way to keep the command repeating??

---

### Post by fake_punk on 2007-12-19
Hmm, I know this is an old post, but there is a switch for wminput that will make it wait until a wiimote is connected.  I am looking to do this as well.
       -r, --reconnect [wait]
              Automatically try reconnect after wiimote disconnect.

       -w, --wait
              Wait indefinitely for wiimote to connect.

---

