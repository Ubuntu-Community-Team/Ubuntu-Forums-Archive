---
title: "How do I install Drupal?"
date: 2006-12-08
forum: General Help
---

### Post by nadavvin on 2006-12-08
Hello

I installed Drupal with apt-get and it installed it in different directory then the www directory.

There no symlink between the two directories like phpmyadmin and I guess it because to serve many website with the same drupal package.

How do I create a website?

Why there no man or info files or any documentation about this?


Is the only solution is to create the symlink myself and edit the files in the other directory and change the permissions to do this?

thanks for your help
Nadav

---

### Post by lhtown on 2006-12-09
If you want it under www, you could just install it manually with a tarball following Drupal's instructions (you can download the tarball and open it to find the install.txt file). It is actually pretty easy if you are able to edit text files and follow instructions and it won't mess up the rest of your system since it doesn't create any dependencies other than what you would already have installed (php, mysql, apache, etc.)

I suspect that the vast majority of people install Drupal manually in order to get the very latest security release. If you rely on the Ubuntu repositories for that type of software, it can be pretty badly out of date.

Happy Drupaling. If you want power without writing a program from the ground up, it is an awesome piece of software. Joomla might be a bit simpler to set up, but it doesn't seem to have the solid base that Drupal has. I recently left Joomla for Drupal mainly because I wanted utf-8 for a mixed language website and I am loving it. 

I still can't get over that I almost missed the taxonomy feature of Drupal by setting up a site I am revising with Joomla.

---

