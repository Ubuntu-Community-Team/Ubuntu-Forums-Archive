---
title: "cryptoApplet.log - logger?"
date: 2006-12-16
forum: General Help
---

### Post by mkor on 2006-12-16
Hi,

I've just found a file in my home folder, called cryptoApplet.log. It was created/modified some time ago and the problem is I do not recall doing anything connected with it... I might have visited some pages about cryptography, but it's rather unlikely that they were Polish - and there is Polish text in the file (see below). The <method> tag's value says "check environment".

Shoul I be worried and start changing all my password etc? Or is it something known and not harmful?

the file's contents:

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE log SYSTEM "logger.dtd">
<log>
<record>
  <date>2006-11-07T19:39:47</date>
  <millis>1162928387647</millis>
  <sequence>0</sequence>
  <logger>CryptoApplet</logger>
  <level>FINER</level>
  <class>com.pwpw.sigctrl.CryptoApplet</class>
  <method>sprawdzSrodowisko</method>
  <thread>10</thread>
  <message>ENTRY</message>
</record>
<record>
  <date>2006-11-07T19:39:47</date>
  <millis>1162928387778</millis>
  <sequence>1</sequence>
  <logger>CryptoApplet</logger>
  <level>FINER</level>
  <class>com.pwpw.sigctrl.CryptoApplet</class>
  <method>sprawdzSrodowisko</method>
  <thread>10</thread>
  <message>RETURN -3</message>
</record>
</log>

---

### Post by mkor on 2006-12-17
Ok, I've read some docs about java class CryptoApplet and Logger... It looks like it's not really a problem and the file format is exactly what Logger class writes to a file, And it's not a "logger" which sends what I type to some listener, but a class used to log application messages to a file.

So, looks like something innocent...

---

### Post by maxamillion on 2006-12-17
It does look innocent, but in the future if you ever have any worries of the sort do a "sudo chmod -rx" to the file and then investigate it further, that way if logs were being appended to the file, the application somewhere doing the logging no longer has the proper access allowed to write to the file and in the strange even it were executable, it will no longer be able to execute.

And in the unlikely event your machine were to be compromised I recommend a low level format of the hard drive before re-installation.

Also, I recommend all users install and run firestarter on their desktops for safe keeping, its a very powerful piece of software and extremely easy to use. Better safe than sorry and if you were to get a logger installed on your machine, it wouldn't be able to broadcast its findings from behind the iptables acl's that firestarter would write. 

/me

---

