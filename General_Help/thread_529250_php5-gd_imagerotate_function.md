---
title: "php5-gd imagerotate function"
date: 2007-08-19
forum: General Help
---

### Post by uniden9 on 2007-08-19
I have search high and low for a solution around  imagerotate function in php-gd, but can not find one. I'm trying to use pre-built captcha addon for a popular webmail client, for an additional layer of security.  I have installed the php5-gd and verified that its loaded in the phpinfo().  But there is an known issue with the gd library, and imagerotate function, of which nothing seems to be happening with.  Is there any work around for this short of compiling and maintaining php myself, which I'd like to avoid? I find it hard enough keeping up to date with apt-get doing all the work, but starting to maintain php myself seems to be a labor intensive task.  Also I'm running ubuntu 7.04.

[Bug #74647 in php5 (Ubuntu) php5-gd not using bundled GD library]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/74647") 

From the php.net manual on the function.
"This function is only available if PHP is compiled with the bundled version of the GD library."
[PHP: imagerotate - Manual]("http://us3.php.net/manual/en/function.imagerotate.php")

Thanks,
Justin.

---

### Post by ratcateme on 2007-12-21
Here check this out it Worked for me :)
[http://au2.php.net/manual/es/function.imagerotate.php#48725](http://au2.php.net/manual/es/function.imagerotate.php#48725)

Scott.

---

