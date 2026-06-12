---
title: "Php ssh2"
date: 2013-05-23
forum: General Help
---

### Post by OldManRiver on 2013-05-23
All,

In order to use ssh2 in PHP, the following installs are needed:

[LIST=1]
[*]Lamp  ==> Full Apache, MySQL, PHP on the Linux box,
[*]PEAR,
[*]phpseclib ==> Extensions for PHP,
[*]
[/LIST]
I got those install correctly and all the libs get called, but getting totally confused by the docs on:

ssh-keygen [option] remotehost [option] localidfile

I need the options to run this twice, once to put into the ~/.ssh/known_hosts file and the other to create the id_rsa file, needed by my php program, since this download script needs to run in cron.

My test code for this is:
```

<?php

	// Test phpseclib functions!
   include ('ftp_config.php');

	//$inc_path = "/usr/share/php/";
	//$new_path = get_include_path();
	//echo "IP=> $inc_path NP=> $new_path \n";
	set_include_path(get_include_path() . PATH_SEPARATOR . 'phpseclib');
	include_once('Net/SSH2.php');
	include_once('Net/SFTP.php');
	include_once('Crypt/RSA.php');
	include_once('Crypt/Hash.php');
	include_once('Math/BigInteger.php');

	$rsa = new Crypt_RSA();
	//$pubKey = file_get_contents('id_rsa.pub');
	//$rsa->setPublicKey($pubKey);
	$priKey = file_get_contents('id_rsa');
	$rsa->loadKey($priKey);

	$sftp = new Net_SFTP('myremoteserver');
	//if (!$sftp->login('myusername', $password)) {
	if (!$sftp->login('myusername', $rsa)) {
	exit("Login Failed\n");
	}
	echo $sftp->pwd() . "\r\n";
	$sftp->put('filename.ext', 'Hello, world!');

?>

```

All help appreciated!

OMR

---

