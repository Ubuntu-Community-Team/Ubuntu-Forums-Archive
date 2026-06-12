---
title: "how to use 'dd' to wipe a usb stick?"
date: 2017-07-30
forum: General Help
---

### Post by wyale on 2017-07-30
I would like to create a usb stick with the boot from usb stick option. In my fantasy, the o/s download will be 1). verified/authenticated and 2). there will be nothing else useful on the stick. So, I was going to overwrite the stick, then download the o/s. How do I use the 'dd' command to overwrite the entire usb stick, for starters?

---

### Post by wyale on 2017-07-30
This looks promising...
[https://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive](https://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive)

---

### Post by Bashing-om on 2017-07-30
wyale; Hello - Welcome to the forum .

Yes that dd command will do . Pay attention to KNOW what the target for dd is !

I like to watch what is going on:
```

dd if=/dev/zero of=/dev/sdX bs=1M status=progress

```
where X is the device name of the target drive.
[INDENT][INDENT]careful is no accident
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-07-30
*Thread moved to** General Help***

---

### Post by HermanAB on 2017-07-30
Hmm, I guess that after the dd with of=/dev/sda, we will not hear from Wyale again...

---

### Post by Bashing-om on 2017-07-31
HermanAB' ouch !

> **HermanAB said:**
> Hmm, I guess that after the dd with of=/dev/sda, we will not hear from Wyale again...

my real bad :(

[INDENT][INDENT]a lapse in thought
[/INDENT][/INDENT]

---

### Post by sudodus on 2017-07-31
**mkusb** wraps a safety belt around **dd**. It helps you identify and select the correct target drive.

See this link, [help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by C.S.Cameron on 2017-07-31
Mkusb +1
of=/dev/sda -1

---

### Post by wyale on 2017-08-03
> **sudodus said:**
> **mkusb** wraps a safety belt around **dd**. It helps you identify and select the correct target drive.

See this link, [help.ubuntu.com/community/mkusb]("https://help.ubuntu.com/community/mkusb")

Thanks for that. Is there a way to see verify the overwrite afterwards, even though it seems to be working?

---

### Post by sudodus on 2017-08-04
You can read the data from the USB stick and check if there is some non-zero byte.

Try with the following commands

```

[SIZE=3]
$ sudo -s

# [COLOR="#cc0000"]< /dev/sd**x** tr -s '\0' ' ' | tr '\000-\255' 'x'| tee /dev/stderr | wc -c[/COLOR]

x1

# exit

[/SIZE]

```

where [COLOR="#cc0000"]**x**[/COLOR] is the drive letter of the USB stick. It will take a long time to scan the whole drive, so be prepared to wait until 'the sed command line' returns to prompt.

If the output is **[SIZE=3]x1[/SIZE]** the drive is overwritten with zeros. There is only one unique byte.

Otherwise there is probably a lot of output, something similar to the following,

```

&#65533;&#65533;xxx&#1084;x&#65533;&#65533;xx&#65533;x&#65533;&#65533;&#65533;xx&#65533;xx&#65533;xx&#65533;x&#65533;xxx&#65533;&#65533;xxxxxx&#65533;xx&#65533;&#65533;xx&#65533;&#65533;x&#65533;x&#65533;x&#65533;xx&#65533;xxxxxxx&#65533;x&#65533;xxx&#65533;&#65533;xxxxxxxxxx
xxxxxxxxxxxxx&#65533;xxxxxxxxxxxxxxxx&#65533;xxxxxxxxxx&#65533;xxxxxxxxxxx&#65533;xx&#65533;xxxxxxxxxxxxx&#65533;xxxx&#65533;xxx&#65533;x
&#65533;xx&#65533;xx&#65533;&#65533;x&#65533;&#65533;x&#65533;x&#65533;&#65533;xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&#65533;xxxxxxxxxxxxxxxx&#65533;xxxxxxxx
xx&#65533;xxxxxxxxxxx&#65533;xx&#65533;xxxxxxxxxxxxx&#65533;xxxx&#65533;xxx&#65533;x&#65533;xx&#65533;xx&#65533;&#65533;x&#65533;&#65533;x&#65533;x&#65533;&#65533;xxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&#65533;
&#65533;&#65533;x&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;xx&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;xxxxxxxxxxxxxxxxxxxxx531

```

and you can stop the process with the hotkey combination

[SIZE=3]*ctrl + c*[/SIZE]

---

