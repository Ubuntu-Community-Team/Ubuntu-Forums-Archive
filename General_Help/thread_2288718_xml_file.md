---
title: "xml file"
date: 2015-07-29
forum: General Help
---

### Post by ray9 on 2015-07-29
I have run into this before and have never been able to figure it out.  How can I turn this file I saved off my phone into something I can read?  xml version='1.0' encoding='UTF-8' standalone='yes' ?> 
<!--File Created By SMS Backup & Restore v7.42 on 23/07/2015 08:07:15--> 
<?xml-stylesheet type="text/xsl" href="sms.xsl"?> 
<smses count="52"> 
  <sms protocol="0" address="8023484352" date="1437430498346" type="1" subject="null" body="Sorry, I am just turning

The file is much longer of course but is there a way to change this format into  something readable?


Thanks

---

### Post by dino99 on 2015-07-29
when digging around "ubuntu read xml file", we can find some related threads like :

[http://askubuntu.com/questions/136809/how-to-open-xmi-files](http://askubuntu.com/questions/136809/how-to-open-xmi-files)

---

### Post by Lars Noodén on 2015-07-31
If you're wanting to rearrange the same XML structures again and again to extract the content, you could look at XLST.  That's one way of rearranging the data wrapped in XML.  Perl has an XML parser, too.

---

