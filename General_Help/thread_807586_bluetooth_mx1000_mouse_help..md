---
title: "bluetooth mx1000 mouse help."
date: 2008-05-25
forum: General Help
---

### Post by no1cares on 2008-05-25
ok i have a bluetooth mouse and when i go to the bluetooth icon right click and select browse devices i see my mouse there.. i highlight in then click connect. i hit the button on my mouse that makes it visible. and wait... it gives me an error 
Couldn't display "obex://[00:07:61:4B:C8:FC]/".
Error: Host down
Please select another viewer and try again.

 i see my mouse listed in both bluetooth preferences (i have it trusted) and in the browse device.. . why wont it work??

---

### Post by no1cares on 2008-05-26
damn, no one seems to know what to do for this....

---

### Post by skeetlz on 2008-05-26
I had this problem with a different bluetooth mouse (Logitech v470) and solved it by reinstalling gnome-vfs-obexftp then unbonding and rebonding the mouse.

Hope this helps!

---

### Post by no1cares on 2008-05-26
where do i do that at?? synaptic package manager??

---

### Post by no1cares on 2008-05-26
> I had this problem with a different bluetooth mouse (Logitech v470) and solved it by reinstalling gnome-vfs-obexftp then unbonding and rebonding the mouse.

installed it and it still isent working... gives me the same error still.

---

### Post by no1cares on 2008-05-26
> I had this problem with a different bluetooth mouse (Logitech v470) and solved it by reinstalling gnome-vfs-obexftp then unbonding and rebonding the mouse.

installed it and it still isent working... gives me the same error still.

---

### Post by no1cares on 2008-05-26
sorry for the double post but i fixed it....

type in terminal
sudo hidd --search
(type password)
Searching....    (make your mouse visible)
connecting to device (whatver the device is.)

---

### Post by eggenspi on 2008-05-28
hello
Thanks for the solution. 
When my computer goes to sleep or hibernate while my mouse is still on, after it wakes up, I have to repeat those things again. Do you know how I can fix this problem too.
Thanks in advance

---

### Post by no1cares on 2008-05-28
have not found out how to prevent that... just have to reconnect it right now...

---

