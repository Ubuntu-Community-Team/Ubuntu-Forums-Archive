---
title: "Help Installing php from source"
date: 2007-03-27
forum: General Help
---

### Post by tamray on 2007-03-27
Looks like I need to install php from source on my 6.10 box. I keep getting the following error:
Warning: preg_match: internal pcre_fullinfo() error -3 in

From googling around the standard answer is:

Don't use external PCRE lib, use bundled instead.


I have apache2 installed, but apt cannot find apache2-devel. How do I find the proper name?

Also, what ./configure options should I pass to php to be sure everything installs properly?

---

### Post by octavianh on 2007-03-28
Just out of curiosity, why are you installing from source?  There are packages available for almost every extension you can think of for the very latest php in synaptic.

---

### Post by tamray on 2007-03-28
Because php has to be compiled specifically with this line:

--with-pcre-regex (excluding any path)

The standard install from apt does not do this, so when you run anything that requires preg_match you get the error I talked about in my post.

I am trying to install gallery2, and the preg_match error is keeping me from finalizing the install.

---

### Post by octavianh on 2007-03-28
Oh, i see, i mistook your error msg to mean you were getting that error on compile, sorry.

---

### Post by lamego on 2007-03-28
You don't need apache2-devel to compile php, you don't even need apache2 at all since it can be used as a client scripting language.
The configure depends on how you install it,  target dirs, and modules.

---

### Post by tamray on 2007-03-28
My apache2 install is in what is called a wre (webgui runtime environment). This folder contains perl, mysql, apache, etc... I thought I had the configuration figured out, but now it is asking for the MySQL header files. Anyway, with that info, how would you configure php, prior to running "make"?

---

### Post by tschneiter on 2007-03-28
Cant you do sudo apt-get install php -O [your options here]?

---

### Post by tamray on 2007-03-28
I didn't know you could do that with apt. what options would you list in this case? I am not sure what features are default, and what need to be listed. I am mainly concerned about installing with mysql support.

---

### Post by codepoetmc on 2007-07-20
Yeah I just did the run around on this one for awhile. You need the header files which are not installed by synaptic by default with mysql apparently. Assuming you're using mysql 5.0.24 use synaptic to install the package named libmysqlclient15-dev. Then set the --with-mysql=/usr/include/mysql (which is where synaptic put the files on my system at least). After doing this I was able to configure and compile php 5.2.3.

Hope this helps

---

