---
title: "opera mime types handling"
date: 2007-07-09
forum: General Help
---

### Post by asipi on 2007-07-09
Hi

I have an annoying problem using opera (though I am an opera-fan for years since 6.22  ).
My current version is 9.22 but the problem exists since ages, Yesterday night I tried to dig
inside it but I could not succeed.

So here comes the details:
Opera: 9.22 nightly build, linux, static qt, deb package
OS: Kubuntu Feisty
Problem: click on some links of files on web pages and/or emails the appropriate assosiated application did not start but Xarchiver tried to open it. Not all of the links, but in the most of the cases. Yesterday I tried to dig deep inside, and tried to find a solution. I tried to attached files in to different emails, one pdf and one pps. The content type of both was application/octet-stream. For the first, opera tried to open it with Xarchiver. Ok, I tried to adjust the mimetype assosiation in opera. I edited the mime setting for application/octet-stream and tried to set it to the KDE's base file handling facility called kfmclient (K file manager client). Kfmclient opened the pdf with evince (what is a gtk based pdf viewer not KDE based  ) and again opened the pps with Xarchiver.
I saved both files into a temp dir and tried to open them with kfmclient with a terminal. Hmmm let me say pdf was opened with Kpdf and pps was opened with OpenOffice. 
I made an other application/octet-stream entry directly for pdf file extension and I adde into the "open with" box kpdf, but still evince opened that.
So what the hell is going on behind opera? How does it give params to the backends? What settings does it use for handling file extensions?
How can I adjust it? And for the first of all: Why does Opera make this so poorly under linux in the 21st century?

Does someone have similar experiences?
REMARK: I have set in an opera ini file the kfmclient as a default file handler...

---

### Post by afternine on 2008-01-09
Hi!

I'm also an Opera fan (since 3,6, yes I know, the years are going by faster than I would like to admit) and a Kubuntu user (a year or so, but still on edgy 6.10, plan to upgrade soon). Did you solve the problem of Opera running the wrong application for some file type? 
I'm also having problems persuading Opera (9.24 Build 671) to open pdf files wtih kpdf instead of kghostview. I tried to set mime type for pdf (application/pdf), set correct file handler (there is a button for this on the same dialog), but without success.

Any tips will be greatly appreciated!

I t

Bye

---

### Post by yupie on 2008-05-10
[http://ubuntuforums.org/showthread.php?p=4926245#post4926245]("http://ubuntuforums.org/showthread.php?p=4926245#post4926245")

---

