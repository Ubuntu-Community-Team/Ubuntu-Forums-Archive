---
title: "[Kubuntu 14.04] Error while manually installing autotools"
date: 2018-12-19
forum: General Help
---

### Post by stuarte83 on 2018-12-19
Hi,
I'm trying to manually istall autotools onto Kubuntu 14.04. I'm still using 14.04 as being one of the (very!) long term unemployed I can't afford even a second hand 64 bit PC;

I have manually downloaded the following packages.

autoconf-2_69_tar_gz     autoconf-2_69_tar_gz_sig
automake-1_15_tar_gz    automake-1_15_tar_gz_sig
libtool-2_4_6_tar_gz       libtool-2_4_6_tar_gz_sig

I'm trying to install these packages according to the advice given on web page [https://askubuntu.com/questions/430706/installing-autotools-autoconf](https://askubuntu.com/questions/430706/installing-autotools-autoconf)

In a terminal, when I issue the command ~/Downloads/Autotools/autoconf$ **tar xf autoconf***
the system displays the following error message **tar: autoconf-2_69_tar_gz_sig: Not found in archive**

After the version number in the archive name, I changed the underscores to periods and issued the same tar command again only for the same error message to be displayed again.

I've had a look at "man tar", in particular the following
-A, --catenate, --concatenate
           append tar files to an archive

Am I supposed to use this option to append the "sig" file to the _tar_gz file ?

If so, why was the "sig" file removed from the _tar_gz file in the first place ?

Thanks in advance for any help that can be given with this.

Best regards,
stuarte83

---

