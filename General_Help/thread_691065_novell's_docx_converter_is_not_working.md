---
title: "novell's docx converter is not working"
date: 2008-02-08
forum: General Help
---

### Post by peleg on 2008-02-08
Hello.

I know that there are many posts about this issue - I know it because I have read at least half of them... but the best and most compact instructions that I've found about installing Novell's docx converter (to read in OO) was here:
[http://www.sigmundvoid.com/?p=81]("http://www.sigmundvoid.com/?p=81")

I have done most if it, in a **slightly** different way: I **didn't** use "alien" because I didn't understand why: my Feisty read rpm's as archives and extract them easily.

So: I have downloaded the rpm from [here]("http://cdn.novell.com/prot/GuM6LMM9SR4~/odf-converter-1.1-7.i586.rpm"), extracted in /home somewhere, and did the 3 cp's:

```

$ sudo cp /home/peleg/Setups/office/usr/lib/ooo-2.0/program/OdfConverter /usr/lib/openoffice/program/
$ sudo cp /home/peleg/Setups/office/usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter
$ sudo cp /home/peleg/Setups/office/usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types

```

OpenOffice was closed during that time. Now, I open OO, try to read the file and get:
> Read-Error.
Data could not be read from this file

Well... I have to admit that I've tried it only on one docx file (I don't have other files in that format) but I do have a very good reason to believe that this file is not corrupted.

I have also read this [thread]("http://ubuntuforums.org/showthread.php?t=386385"), and typed:
```
$ md5sum /usr/lib/openoffice/program/OdfConverter /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu
```

and got:
```
a9c0b6d9d1ea74a85abeb82d3b03ae77  /usr/lib/openoffice/program/OdfConverter
0c31809b793c597407ce7231b3750c7e  /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu
370a57074d97c013927228e273364e52  /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu
```

maybe because the OdfConverter file itself is of newer version (?).

I am using the default OpenOffice pack that comes with Feisty (2.2).

***By the way - this file is NOT private - in the meanwhile, if someone could convert it for me, I will be very thankful!*** It is math questions sheet that I want to solve in order to practice for the numerical analysis exam I have in a few days... ;-)

Could someone advice?

Thanks ahead,
Peleg.

---

### Post by -grubby on 2008-02-08
Well I can't help you with the problem that program had, but, here's a [website]("http://docx-converter.com/") to convert them

---

