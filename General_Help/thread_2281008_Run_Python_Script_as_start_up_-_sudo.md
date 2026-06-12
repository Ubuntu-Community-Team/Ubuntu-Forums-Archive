---
title: "Run Python Script as start up - sudo"
date: 2015-06-03
forum: General Help
---

### Post by elliotbeken on 2015-06-03
Hi all,

I am very new to Python scripting and i am starting to have a play as i have a Raspberry PI.

I have written a simple script that makes some LEDs flash. I am looking how i can get this to run at startup (so i dont have to manually run the script)

Currently to run the script i run the following command:

'sudo python blink2.py'

is there a way this can be done ? it has to run a sudo/root.....

Many Thanks

---

### Post by papibe on 2015-06-03
Hi elliotbeken.

You could use the root crontab, and use the @reboot custom tag:
```
sudo crontab -e
```
And then add something like:
```
@reboot /path/to/script.py
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by elliotbeken on 2015-06-03
Hi papibe,

Nope this didnt work ! 

I added this:

@reboot /home/elliot/blink3.py

any ideas ? 

Thanks

---

### Post by elliotbeken on 2015-06-08
Managed to work this out ! Quite simple really placed this in the rc.local

python /home/elliot/blink3.py

---

### Post by papibe on 2015-06-08
Glad you worked it out :D

I few tips:

Since this file is a little 'touchy', I'd recommend:
[LIST]
[*]Using full paths.
[*]Force a 'positive ending'.
[*]Assume minimal environment on your script (some environment variables may not be available).
[*]Don't forget the 'exit 0' line.
[/LIST]
So the last line would be something like:
```
/usr/bin/python /home/elliot/blink3.py || /bin/true
exit 0
```
Regards.

---

