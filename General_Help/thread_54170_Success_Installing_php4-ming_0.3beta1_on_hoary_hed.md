---
title: "Success Installing php4-ming 0.3beta1 on hoary hedgehog!"
date: 2005-08-03
forum: General Help
---

### Post by Pedro Sacramento on 2005-08-03
I finnally had success installing the "ming0.3beta1" swf library for php 4.3.1 on Ubuntu 5.04 (hoary)! You can download the .deb file from:

[http://klaus.geekserver.net/debian/binary/php4-ming_0.3beta1-3_i386.deb](http://klaus.geekserver.net/debian/binary/php4-ming_0.3beta1-3_i386.deb)

Use the terminal to enter the directory where you downloaded the .deb file and type:

#dpkg --install php4-ming_0.3beta1-3_i386.deb

For those using command line php (php-cli):

#gedit /etc/php4/cli/php.ini

And for those using php under apache2:

#gedit /etc/php4/apache2/php.ini

Search for ".so" on "php.ini"

Insert it inside you file, near something like "extension=gd.so":
extension=php_ming.so

If under apache, you'll need to restart apache:
#/etc/init.d/apache2 restart

Done!

If you want to make a test, there's a sample php file, that will creates a swf file containing a red square:

<?
// code by gazb : gazb dot ming at NOSPAM gmail dot com
// August 2004
// [http://www16.brinkster.com/gazb/ming/](http://www16.brinkster.com/gazb/ming/)
Ming_setScale(20.00000000);
ming_useswfversion(6);
$movie=new SWFMovie();
$movie->setDimension(550,400);
$movie->setBackground(0xcc,0xcc,0xcc);
$movie->setRate(12); 
$squareshape=new SWFShape(); 
$squareshape->setRightFill(255,0,0); 
$squareshape->drawLine(100,0);  
$squareshape->drawLine(0,100); 
$squareshape->drawLine(-100,0); 
$squareshape->drawLine(0,-100); 
$squaresymbol=$movie->add($squareshape);
$squaresymbol->moveTo(100,100);
$movie->save("square.swf");
?>

This forum is helping me very much, hope it helps too(and excuse me for my bad english)
See ya

---

