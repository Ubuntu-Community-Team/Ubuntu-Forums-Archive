---
title: "issue with PDF files in Xubuntu"
date: 2019-09-06
forum: General Help
---

### Post by said-el on 2019-09-06
I have installed Xubuntu 18.04 LTS , but I have an issue with pdf files. after installing WPS office , all pdf files (even downloaded files) now have the type : application/wps-office.pdf, and they are not recognized by browsers . here attached screenshot :

Thunar showing pdf document as Microsoft word

Nemo is showing pdf document type as : Unknown (Application/wps-office.pdf)

Chrome and Firefox don't recognize pdf files

Please help

---

### Post by dragonfly41 on 2019-09-06
In Ubuntu 16.04 mime types are found in /etc/mime.types

e.g.
application/pdf					pdf

What do you see when you search "pdf"?

---

### Post by ajgreeny on 2019-09-06
See if you can overcome this problem, which I have never seen before, by right clicking on a PDF file in thunar file-manager, going to Properties, and in the "Open With" drop-down box choose Document-Viewer.  I suspect at the moment it may show that WPS-Office is the default.

I haven't used WPS-Office, but it appears that it has taken over as the default application for opening any PDF files on your system.

PS:
Please do not add images inline as you did; either add them as attachments using the paperclip icon in the text entry toolbar or simply as links to images as they now are.

---

### Post by said-el on 2019-09-06
When I search for pdf in /etc/mime.types I have this
**application/pdf					pdf**
[B]application/wps-office.pdf					pdf

[/B]

---

### Post by said-el on 2019-09-06
I did, still the same issue, but I noticed something: 
if the file is named document.pdf , the type shown in file propriety is :  **Unknown (application/wps-office.pdf)**
if the fine is named document, the type shown is  : **Document (application/pdf)**

---

### Post by dragonfly41 on 2019-09-06
I would comment out line **application/****wps****-office.****pdf    ****pdf**
You may have to log out / log in for change to have effect

---

### Post by said-el on 2019-09-06
Just did, nothing happened , still the same issue.
Even downloaded files from the internet show the type as **Unknown (application/wps-office.pdf)**

---

### Post by said-el on 2019-09-06
Ok it's solved, I installed evince, and made it default pdf viewer, now everything is working fine
thnx everyone

---

### Post by slickymaster on 2019-09-06
> **said-el said:**
> Ok it's solved, I installed evince, and made it default pdf viewer, now everything is working fine
thnx everyone

Being that the case, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

