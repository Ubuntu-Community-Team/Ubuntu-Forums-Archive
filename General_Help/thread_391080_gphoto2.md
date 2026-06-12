---
title: "gphoto2"
date: 2007-03-22
forum: General Help
---

### Post by BertjeBebo on 2007-03-22
Hi,

I use Kubuntu Edgy and have a kodak c330 digital camera (usb). It used to work by uploading via Digikam, but not anymore. 

via command-line i still can upload pictures with gphoto2, but only with 'sudo'

sudo gphoto2 -P


gphoto2 -P doesn't work and I get a io-library error


i suppose it has something to do with privileges, but no idea how to fix

all help is welcome

---

### Post by llamakc on 2007-03-22
It's a bug.

Here's a way around it for now (on Edgy)

Open a terminal. Type:

```

sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

```Now, comment OUT the line that reads:

```

BUS!="usb*", GOTO="libgphoto2_rules_end"

```and ADD in a line beneath it that reads:

```

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```And finally restart udev:

```

sudo /etc/init.d/udev restart

```

---

### Post by BertjeBebo on 2007-03-23
ok, thanks ... i'd tried this fix already but i didn't work ... maybe I'd mistaked somewhere ... i'll give it another try this weekend

i'm not in a hurry anymore, just before bedtime I read about another workaround by downgrading libgphoto :)

---

