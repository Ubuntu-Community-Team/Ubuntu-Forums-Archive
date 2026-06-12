---
title: "How to start emacspeak from inside emacs."
date: 2018-02-03
forum: General Help
---

### Post by porparek on 2018-02-03
Hi,
How can I start emacspeak from inside emacs. I know that I may run emacspeak just by typing emacspeak in bash but I want to run emacspeak occasionally. So I want to run emacs first and then from time to time run emacspeak in it - without exiting emacs. I tried the following command in emacs:
load-file /usr/share/emacs/site-lisp/emacspeak/lisp/emacspeak-setup.el

but I get the message "Process speaker not running" and cannot hear any speech.
I use Xubuntu 16.04 with speech-dispatcher enabled.
Great thanks for help.

---

### Post by alexarnaud on 2018-03-18
Do you have find a solution for your issue?

Best regards,
Alex.

---

### Post by porparek on 2018-05-20
Yes.
Please set the following env variables before launching emacs:
export DTK_PROGRAM=espeak
export DTK_TCL=tcl
export DTK_PORT=none
export DTK_DEVICE="espeak"

Now launch emacs and just load file in it as follows to launch emacspeak:
M-x load-file /usr/share/emacs24/site-lisp/emacspeak/lisp/emacspeak-setup.el

You may also just replace the following in /usr/bin/emacspeak:
#exec emacs24 -l /usr/share/emacs24/site-lisp/emacspeak/lisp/emacspeak-setup.el $CL_ALL
exec emacs24 $CL_ALL

Now you may start emacspeak and load file in it as follows to launch emacspeak:
M-x load-file /usr/share/emacs24/site-lisp/emacspeak/lisp/emacspeak-setup.el

Best Regards

---

