---
title: "phpmyadmin: generic_init failed in mcrypt.lib.php on line 90"
date: 2005-04-21
forum: General Help
---

### Post by smarttaz on 2005-04-21
Hoary:
Apache/2.0.53 (Ubuntu) mod_python/3.1.3 Python/2.4.1 PHP/4.3.10-10ubuntu4 mod_ssl/2.0.53 OpenSSL/0.9.7e
[u]
[http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/")[/u] 
[b]
Fatal error: generic_init failed in /usr/share/phpmyadmin/libraries/mcrypt.lib.php on line 90[/b]

which is:
return trim(mcrypt_decrypt(MCRYPT_BLOWFISH, $secret, base64_decode($encdata), MCRYPT_MODE_CBC, $iv));

But phpinfo() gives:

 ```
			mcrypt
mcrypt support	enabled
version 	>= 2.4.x
Supported ciphers 	
			cast-128 gost rijndael-128 twofish arcfour 
			cast-256 loki97 rijndael-192 saferplus wake 
			blowfish-compat des rijndael-256 serpent 
			xtea blowfish enigma rc2 tripledes
Supported modes 	cbc cfb ctr ecb ncfb nofb ofb stream


Directive	Local Value	Master Value
mcrypt.algorithms_dir	no value	no value
mcrypt.modes_dir	no value	no value

Directive	Local Value	Master Value
mcrypt.algorithms_dir	no value	no value
mcrypt.modes_dir	no value	no value

``` 

What is to be done for my **phpMyAdmin** to work???

PHP works;
MySQL works, mysql-admin too;
Apache2 works (but cannot fix SSL to work).

---

### Post by miscreant on 2005-07-24
I see this is old, so it's likely you already know the answer to this, but for any people who stumble upon this with the same problem. Chances are that in your config.inc.php file you did not set anything for the $cfg['blowfish_secret'] variable. If you're using cookie authentication, the this value needs to be set to something. Doesn't really matter what, just something to encrypt the cookies with.

miscreant

---

### Post by smarttaz on 2005-07-25
[QUOTE=miscreant]I see this is old, so it's likely you already know the answer to this, but for any people who stumble upon this with the same problem. Chances are that in your config.inc.php file you did not set anything for the $cfg['blowfish_secret'] variable. If you're using cookie authentication, the this value needs to be set to something. Doesn't really matter what, just something to encrypt the cookies with.
 
miscreant[/QUOTE]
Thank you, I'll try this at home, on that installation which still has this issue (an older laptop).
 
Ubuntu has the very bad choice of NOT having PHP+MySQL+Apache +/- phpMyAdmin **on the CD**, and... of NOT having them working unless you waste some time for configuring them. (in SuSE they work "right out of the box" if you're installing them). 
 
Rumors circulate saying that, for instance, Breezy final will have Mono not only in main, but on the CD!
**IF** Breezy will have MONO on the CD and still NO improvement over the LAMP issue, I'll switch back to some older distro, because this will mean Ubuntu will have lost its way and this is not the Linux way!

---

