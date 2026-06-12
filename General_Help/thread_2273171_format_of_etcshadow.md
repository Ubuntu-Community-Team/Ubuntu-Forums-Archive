---
title: "format of /etc/shadow"
date: 2015-04-11
forum: General Help
---

### Post by kimble2 on 2015-04-11
Ubuntu 14.04
The salt and hash fields for each user seem to be stored base64-encoded. I have tried to untangle this with PHP, but it still doesn't match. Is there a password stretch involved too?  Where is this written up?

```
<?php
$username = "!!!!";
$password = "!!!!";
print "PHP version = ".phpversion()."\n";
$algos = array(0, "MD5", "2", "3", "4", "5", "SHA-512");
//
$file = file_get_contents("/etc/shadow");
$lines = explode("\n", $file);
for($i=0; $i<count($lines); $i++)
{    $fields = explode(":", $lines[$i]);
    if($fields[0] == $username)
    {    $subfields = explode("$", $fields[1]);
        $algo = $subfields[1];
        $salt = $subfields[2];
        $hash = $subfields[3];
        break;
    }
}
print "algo = $algos[$algo]\n";
print "salt = $salt\n";
print "stored hash = \n$hash\n";
print base64_encode(hash("sha512", $password.base64_decode($salt), true))."\n";
print base64_encode(hash("sha512", base64_decode($salt).$password, true))."\n";
?>
```


PHP version = 5.5.9-1ubuntu4.7
algo = SHA-512
salt = rwslJbfH
stored hash = 
4POoBvIkJ1L6uY5UUTUoPPrXqdH025a9.yFQR72EDx73tPPlm/IkNG8JYad4Lk6I.AUsFDtJ1zRUQFMgy8dcR/
32j4Z7LzLhilqeX1PJK5eTcabEXfi8Ofr2wGj/5MSBPK0f2QSv48v4pHorXp/OiJiV4S/hxRx4alGiCk4H7gwQ==
lO6JEiRnkAYi5mHOp7HqnoQmmtmalppBWyiY3pIwbSyK5svLpv60/p5U86h7RJ88Pcq8XYf+k4Gyh9n3b3KiEQ==

---

### Post by Holger_Gehrke on 2015-04-11
'man 5 shadow', 'man 3 crypt' and [http://www.gnu.org/software/libc/manual/html_node/crypt.html](http://www.gnu.org/software/libc/manual/html_node/crypt.html). It's not base64, crypt() has it's own code to force it's results into the printable range of characters. PHP has a crypt() function ([http://php.net/manual/en/function.crypt.php](http://php.net/manual/en/function.crypt.php)) that used to be a wrapper around the function in libc, but uses it's own implementation of this algorithm since Version 5.3.

---

### Post by kimble2 on 2015-04-11
Thanks - that gets me into the right area at least.
I still can't get PHP to produce a hash from a password that matches the hash stored in /etc/shadow .
Those man pages still don't make it clear whether the salt is the actual printable string or the original (presumably shorter) string that has been turned into a printable string.
- and how to recover the original string.
Surely there must be a write-up of this vital security area by Ubuntu for 14.04

---

