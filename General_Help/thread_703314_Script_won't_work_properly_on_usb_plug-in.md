---
title: "Script won't work properly on usb plug-in"
date: 2008-02-21
forum: General Help
---

### Post by xplode_me on 2008-02-21
I have this script ran automagically by udev if I plug my usb pendrive. The question is, it will output the "date >> /home/kiosk/usb.log" thing, but it won't execute the prior "cp -R" part.

Can anyone help, i'm out of ideas.

```
#!/bin/bash
if [ "${ACTION}" == "add" ] && [ -f "${DEVICE}" ]
then
sleep 5 && cp -R /media/KIOSK/flash /home/kiosk/.kiosk/
DISPLAY=:0 /usr/bin/zenity --info --text "Processo concluido com sucesso,
obrigado!\nPor favor reinicie o computador."
date >> /home/kiosk/usb.log
fi
```

---

### Post by freelinuxhelp on 2008-02-21
I think I would move the cp -R part to its own line and remove the &&

---

### Post by xplode_me on 2008-02-21
> **freelinuxhelp said:**
> I think I would move the cp -R part to its own line and remove the &&

That gives me the same output.

---

### Post by freelinuxhelp on 2008-02-21
can you post the output?

---

### Post by xplode_me on 2008-02-21
There is no visible output except for the "date >> log" line.
So it reaches that line, but the others aren't properly executed?...

---

### Post by freelinuxhelp on 2008-02-21
This is from a flash drive right? Mine automounts as /media/usbdisk. You might check that.

When I troubleshoot my scripts, I put an echo statement and a pause after each line that I question.
Like this:
```
#!/bin/bash
if [ "${ACTION}" == "add" ] && [ -f "${DEVICE}" ]
then
sleep 5
cp -R /media/KIOSK/flash /home/kiosk/.kiosk/

echo "CP Command Complete. Check."
pause

DISPLAY=:0 /usr/bin/zenity --info --text "Processo concluido com sucesso,\
obrigado!\nPor favor reinicie o computador."
date >> /home/kiosk/usb.log
fi
```

---

### Post by xplode_me on 2008-02-22
Well, the problem is that this script is running before there is any mount point to copy from. And the sleep thing delays the mounting too.

So, it doesn't work this way, because at the time of the "cp" there is no mount point to copy from.
If i "/etc/init.d/udev restart" then it works (the mount point is there). Also the GUI part still does nothing (zenity).


Any ideas?

---

### Post by xplode_me on 2008-02-24
Any idea for a solution?

---

### Post by Beefeater on 2008-02-24
Something like this might work, haven't tried it.
```

#!/bin/bash
while :
do
if [ -d /media/KIOSK/flash ];
then
	cp -R /media/KIOSK/flash /home/kiosk/.kiosk/
	DISPLAY=:0 /usr/bin/zenity --info --text "Processo concluido com sucesso,
	obrigado!\nPor favor reinicie o computador."
	date >> /home/kiosk/usb.log
	exit
fi
done
```

---

### Post by freelinuxhelp on 2008-02-24
seems like line 7 might be off. shouldnt it be:
DISPLAY=:0 ; /usr/bin/zenity --info --text "Processo concluido com sucesso,\

?

---

### Post by Beefeater on 2008-02-25
> **freelinuxhelp said:**
> seems like line 7 might be off. shouldnt it be:
DISPLAY=:0 ; /usr/bin/zenity --info --text "Processo concluido com sucesso,\

?

Cut and paste :-) Something went wrong

---

### Post by freelinuxhelp on 2008-03-08
How are things with this issue now?
Everything resolved?

---

