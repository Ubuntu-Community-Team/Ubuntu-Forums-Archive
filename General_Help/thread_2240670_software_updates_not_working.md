---
title: "software updates not working"
date: 2014-08-21
forum: General Help
---

### Post by Levi_Johnston on 2014-08-21
I am trying to update my software in the software updater and its not working it says "an unhadlable error occurred There seems to be a programming error in the aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks." I am on the Asus X550la with an i5 and 4 GB of ram and I am using a bootable USB drive

---

### Post by grahammechanical on 2014-08-21
Open a terminal and run these two commands

```
sudo apt-get update
sudo apt-get upgrade
```

and post all error messages in this thread.

---

### Post by Levi_Johnston on 2014-08-21
I uploaded a picture of the errors on megaupload because its too much to type out [https://mega.co.nz/#!SQdgmJYA!cMyNZ3nldDwEoEJHwcfps8bbQVSnTZhoYP36Zz22tHc](https://mega.co.nz/#!SQdgmJYA!cMyNZ3nldDwEoEJHwcfps8bbQVSnTZhoYP36Zz22tHc)

---

### Post by grahammechanical on 2014-08-21
I am sorry but I am not going to download a 3.4 MB image to my machine.

---

### Post by Levi_Johnston on 2014-08-21
That's completely understandable. I cropped it and compressed it to 600kb

[https://mega.co.nz/#!WQUmFIAD!E3q6ja7dxiwpuhcvl7P5SXYJyikws3TxM37mhWZO2OA](https://mega.co.nz/#!WQUmFIAD!E3q6ja7dxiwpuhcvl7P5SXYJyikws3TxM37mhWZO2OA)

---

### Post by Levi_Johnston on 2014-08-21
Also my touchpad doesn't work and I think its a kernel issue so I tried to upgrade my kernel in the terminal and that didn't work either

---

### Post by sammiev on 2014-08-21
Just use the # symbol from above and copy and paste your info between the "[CODE data here /CODE]"

---

### Post by lisati on 2014-08-21
> **sammiev said:**
> Just use the # symbol from above and copy and paste your info between the "[CODE data here /CODE]"

An alternative for jpg files is to upload the image as an attachment. If you scroll down the screen while typing your reply, you should see a button "manage attachments" which can be used for this.

---

### Post by Levi_Johnston on 2014-08-21
[ATTACH=CONFIG]255706[/ATTACH]Thank you! Sorry I was on the mobile site and I didn't see that option

---

### Post by Jessie_James_A._At on 2014-08-21
try this in terminal:

$ sudo rm /var/lib/apt/lists/* - vf
$ sudo get-apt updates

that was happen before  me, but i solve it tru that command above

---

