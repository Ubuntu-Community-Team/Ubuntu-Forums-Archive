---
title: "Freeguide/XMLTV"
date: 2005-07-13
forum: General Help
---

### Post by lordgibbness on 2005-07-13
Hi,

Up until recently I was using DigiGuide as a TV scheduler on my Windows box, but I now want to use a free alternative based on XMLTV. I found Freeguide, which works well and so I decided to install it on my Linux box.

Now that went ok-ish.

I found the .rpm file which I downloaded from sourceforge and alien'd it into a .deb file, which I installed. It is a java program, but the xmltv part seems to use perl.

When I run the updater it errors with: Can't call method "contents" on an undefined value at /usr/bin/tv_grab_uk_bleb line 180.

This line is to do with reading the contents of a zip file. Looking around the net I found about runnning:

sudo perl -MCPAN -e shell

and doing an install Compress::Zlib - but it doesn't work as it errors with a Zlib.c command not found error.

(Before this error had occurred, I had a Zip.pm error which I had to fix with an install Archive::Zip command)

Does anyone know where I am going with all this? Is it XMLTV or Perl or Freeguide or Zlib that is not installed properly?

Thanks and sorry for the bad description!

---

### Post by lordgibbness on 2005-07-14
Does anyone know how I can install Compress::Zlib from within Perl CPAN?

I keep getting a Zlib.c error. Is it a broken Zlib.c file?

Thanks.

---

### Post by lordgibbness on 2005-07-19
Hi,

Has anyone ever had any problems in this area? Does anyone want to give freeguide a go to see if they can get it working?

Thanks.

---

