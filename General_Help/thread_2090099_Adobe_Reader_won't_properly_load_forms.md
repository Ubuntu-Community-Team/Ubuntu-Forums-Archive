---
title: "Adobe Reader won't properly load forms"
date: 2012-12-01
forum: General Help
---

### Post by 73ckn797 on 2012-12-01
Running 12.04 64bit.
I have installed the Adobe Reader 9.5.1 from the Adobe web site. I used the .deb file.

The following error displays: ```
postMessage() threw Error: name=TypeError message=PDFObject.postMessage is not a function
```The pdf forms I must use allow me to enter info in fields for a report form. These forms can be saved and uploaded back to the source for the report submission.

The form will load after acknowledging the error but it contains no information, it is a blank form. The same Adobe Reader is installed on another computer running 12.04 32bit and it works just fine.

I have seen many posts around the Internet of people having problems with the Adobe reader in Ubuntu 64 bit. The version in the Medibuntu repositories does not work either. It raises the same error message whether it is a 32 or 64 bit install.

Any suggestions?

---

### Post by rnerwein on 2012-12-01
> **73ckn797 said:**
> Running 12.04 64bit.
I have installed the Adobe Reader 9.5.1 from the Adobe web site. I used the .deb file.

The following error displays: ```
postMessage() threw Error: name=TypeError message=PDFObject.postMessage is not a function
```The pdf forms I must use allow me to enter info in fields for a report form. These forms can be saved and uploaded back to the source for the report submission.

The form will load after acknowledging the error but it contains no information, it is a blank form. The same Adobe Reader is installed on another computer running 12.04 32bit and it works just fine.

I have seen many posts around the Internet of people having problems with the Adobe reader in Ubuntu 64 bit. The version in the Medibuntu repositories does not work either.

Any suggestions?
id did the same as you but on a 64 bit Ubuntu 12.04.1 release.
what i get when i start the acroread are a lot of error messages
(acroread:9656): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(acroread:9656): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

and so on.
but if it is poped up - it works well

---

### Post by 73ckn797 on 2012-12-01
> **rnerwein said:**
> id did the same as you but on a 64 bit Ubuntu 12.04.1 release.
what i get when i start the acroread are a lot of error messages
(acroread:9656): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: falsche ELF-Klasse: ELFCLASS64

(acroread:9656): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

and so on.
but if it is poped up - it works well
Are you using the Medibuntu version or from Adobe? Medibuntu version is 9.4 and the Adobe version is 9.5

---

### Post by rnerwein on 2012-12-01
> **73ckn797 said:**
> Are you using the Medibuntu version or from Adobe? Medibuntu version is 9.4 and the Adobe version is 9.5
i told you i did the same as you - i have downloaded:
adobe-reader-9-5-1-en-ubu.deb
cheers

---

### Post by 73ckn797 on 2012-12-01
> **rnerwein said:**
> i told you i did the same as you - i have downloaded:
adobe-reader-9-5-1-en-ubu.deb
cheers
I read what you said. Do you have any solution(s) to offer?

---

### Post by rnerwein on 2012-12-02
> **73ckn797 said:**
> I read what you said. Do you have any solution(s) to offer?

sorry - no

---

