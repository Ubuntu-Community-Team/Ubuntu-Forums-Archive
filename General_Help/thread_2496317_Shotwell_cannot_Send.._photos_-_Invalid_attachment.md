---
title: "Shotwell cannot Send.. photos - Invalid attachment fd passed"
date: 2024-03-23
forum: General Help
---

### Post by Milan Knizek on 2024-03-23
Hi,

Ubuntu 23.10, fresh installation. Shotwell is a snap package.

When the user wants to Send the selected photo to Evolution New mail window as an attachment, the following error appears and the photo is not sent to Evolution:

[FONT=Courier New]Shotwell
Cannot send file dscf5225_1.jpg,
GDBus.Error:org.freedesktop.portal.Error.InvalidArgument: Invalid attachment fd passed
OK (button)[/FONT]

Googling did not help much. In prior version of Ubuntu 22.04.4 LTS, the "Send" feature worked as expected. (Shotwell was not a snap package, if I recall correctly.)

Any idea how to resolve the bug?

---

### Post by HermanAB on 2024-03-24
Simple - don’t use Snap packages. To me, it is simply not worth the hassle of trying to figure out how to make them work right.

---

### Post by Milan Knizek on 2024-03-24
Good point.
I have googled a bit more and it seems many applications have broken functionalities once they are installed via snap. Either a misconfigured snap or preference of security over usability.
In either case, I moved back to apt Shotwell package.

---

### Post by HermanAB on 2024-03-25
Yup - snap packages tend to be immature and untested, so snapd is one of the things I uninstall on Ubuntu.  

Canonical is trying its level best, but has a problem with a lack of QA. There is no glamour in QA and it is always the Cinderella of engineering projects.

Looking around me, everything I have now - ‘cept for macbooks - is running Devuan Linux.

---

