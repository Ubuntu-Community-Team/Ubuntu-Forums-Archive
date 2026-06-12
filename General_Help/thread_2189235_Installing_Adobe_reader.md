---
title: "Installing Adobe reader?"
date: 2013-11-21
forum: General Help
---

### Post by grier-devon on 2013-11-21
Hello Everyone,
So I am trying to install Adobe Reader, I mainly need this since I am taking a class where when I download the book and it is in PDF it is locked by username and password but the Linux document viewer will only prompt me for a password and not the username so therefore cannot access the PDF.

I have done some googling and have tried numerous guides and other post on the subject from this forum and nothing is working. Please help me get Adobe Reader installed on Ubuntu 13.10 64 Bit.

---

### Post by philinux on 2013-11-21
Install gdebi package first. Then get the deb file [http://get.adobe.com/uk/reader/otherversions/](http://get.adobe.com/uk/reader/otherversions/)

Open it with gdebi.

---

### Post by fantab on 2013-11-21
Have you enabled 'Canonical Partner' repositories and tried to install 'acroread'?

---

### Post by philinux on 2013-11-21
> **fantab said:**
> Have you enabled 'Canonical Partner' repositories and tried to install 'acroread'?

It's gone from there now unfortunately in 13.10.

And I believe linux support has gone too apart from security updates to current linux version. Gone the same way as adobe flash.

---

### Post by fantab on 2013-11-21
> **philinux said:**
> It's gone from there now unfortunately in 13.10.

And I believe linux support has gone too apart from security updates to current linux version. Gone the same way as adobe flash.

Thanks for the info phil, I didn't know that. I haven't used it since 12.04. I switched to PDFXChange through WINE for purposes of commenting & highlighting. And in my ARCH I am using Okular, which is not bad...
I feel Linux badly needs a good PDF reader which is atleast as good as Adobe Reader for Linux was. I sometimes do feel frustrated working with PDFs in Linux.

Regards...

---

### Post by philinux on 2013-11-21
@fantab - I not tried it yet but I believe okular is quite good.

Apart from all the packages it wants to install on gnome.

---

### Post by fantab on 2013-11-21
> **philinux said:**
> @fantab - I not tried it yet but I believe okular is quite good.

Apart from all the packages it wants to install on gnome.

With all those packages and libraries its download and install size matches acroread. So far I haven't had any conflicts with gnome.
**Size-   154.54 MiB** in arch.
And the total installed size is less than Adobe, AFAIK.

---

### Post by grier-devon on 2013-11-21
Hey everyone thanks for the support, install went great. Issue is these PDF require a username and password and Adobe 9 is not supporting them. I might give okular a try and see if it can do it and if not I guess I will have to open them using Adobe Reader 11 on my Windows VM, I just hate using that thing cause I have a mobile i3 with 4 GB of memory  so it slows everything down. Thanks everyone.

---

### Post by philinux on 2013-11-21
> **grier-devon said:**
> Hey everyone thanks for the support, install went great. Issue is these PDF require a username and password and Adobe 9 is not supporting them. I might give okular a try and see if it can do it and if not I guess I will have to open them using Adobe Reader 11 on my Windows VM, I just hate using that thing cause I have a mobile i3 with 4 GB of memory  so it slows everything down. Thanks everyone.

If you've got the password then pdftk can open it.

I think there are other pdf apps that can do it too in synaptic or software center.
> If PDF is electronic paper, then pdftk is an electronic stapler-remover, hole-punch, binder, secret-decoder-ring, and X-Ray-glasses. Pdftk is a simple tool for doing everyday things with PDF documents. Keep one in the top drawer of your desktop and use it to:
 - Merge PDF documents
 - Split PDF pages into a new document
 - Decrypt input as necessary (password required)
 - Encrypt output as desired
 - Fill PDF Forms with FDF Data and/or Flatten Forms
 - Apply a Background Watermark
 - Report PDF on metrics, including metadata and bookmarks
 - Update PDF Metadata
 - Attach Files to PDF Pages or the PDF Document
 - Unpack PDF Attachments
 - Burst a PDF document into single pages
 - Uncompress and re-compress page streams
 - Repair corrupted PDF (where possible)

---

### Post by grier-devon on 2013-11-21
The issue is it prompts me for the password but i think what is messing it up is I am not being prompted for my username. I am not sure what username it is using. I will give those a try hope for the best, I just need one to prompt me for a username and password.

---

### Post by philinux on 2013-11-21
> **grier-devon said:**
> The issue is it prompts me for the password but i think what is messing it up is I am not being prompted for my username. I am not sure what username it is using. I will give those a try hope for the best, I just need one to prompt me for a username and password.

search net for ubuntu pdf find username password

---

### Post by cluelesswonder on 2014-05-07
Installed acrocread on 14.04 to read XFA files that I couldn't seem to open with any other application (tried Evince, Okular, Master PDF editor). Acroread works so far! Thanks for the responses on this post :p

---

