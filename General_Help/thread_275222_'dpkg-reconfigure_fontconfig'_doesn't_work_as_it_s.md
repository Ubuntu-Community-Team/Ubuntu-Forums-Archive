---
title: "'dpkg-reconfigure fontconfig' doesn't work as it should."
date: 2006-10-11
forum: General Help
---

### Post by quvil on 2006-10-11
Hello everybody.

Often when people answer questions about font problems I see them say:

"run 'sudo dpkg-reconfigure fontconfig' and when asked about...."

The problem is that when I ran that command nothing is asked. What I get as an output is:

------------------------------------------------------------
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
W: Following package's configuration script returned error(1) during doing do-install-real.
  Package: fontconfig
  Category: type1
  Installing Font: /usr/share/fonts/type1/gsfonts/n021024l.pfb
  Installing ID: NimbusRomNo9L-MediItal
Defoma has set this font as 'exclude' to keep it from being installed.
You can still have it installed by unsetting the 'exclude' mark after the cause of the error gets removed.

[here comes a large bunch of similar warnings as above]

Updating category cid..
Regenerating fonts cache... done.
------------------------------------------------------------


and that's all. Recently i upgraded to Edgy, but the situation didn't change.

What is a problem here?

---

### Post by Jeremy23 on 2006-10-11
I got the same problem, but managed to achieve what I intended by putting my configuration in /etc/fonts/local.conf.

If you wanted to activate Autohinting, here is the code for /etc/fonts/local.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
<!-- If the font is bold, turn off autohinting -->
<match target="font">
 <test name="weight" compare="more"><const>medium</const></test>
 <edit mode="assign" name="autohint"><bool>false</bool></edit>
</match>
</fontconfig>
```

---

### Post by quvil on 2006-10-11
> **Jeremy23 said:**
> I got the same problem, but managed to achieve what I intended by putting my configuration in /etc/fonts/local.conf.

If you wanted to activate Autohinting, here is the code for /etc/fonts/local.conf

No, there is another problem - I want to enable bitmapped fonts. And actually even if it is possible to configure whatever I need by changing configuration files, I would have liked to fix the problem with wrong behavior of dpkg-reconfigure.

---

### Post by quvil on 2006-10-11
Ok, I am answering to myself: instead of "sudo dpkg-reconfigure fontconfig" it should be "sudo dpkg-reconfigure fontconfig-config".

It is a good idea to use google rather more than *I* did  :).

---

### Post by Jeremy23 on 2006-10-11
> **quvil said:**
> Ok, I am answering to myself: instead of "sudo dpkg-reconfigure fontconfig" it should be "sudo dpkg-reconfigure fontconfig-config".

It is a good idea to use google rather more than *I* did  :).

Ah, thanks for the help. I'm glad to know my question was answered. Er, hang on, who was asking the question? :D

---

