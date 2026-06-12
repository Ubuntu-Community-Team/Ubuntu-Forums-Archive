---
title: "Apache Problem"
date: 2013-03-04
forum: General Help
---

### Post by ooseven on 2013-03-04
I have the same problem. I'm 1 day newbie at this.

This is what I get when I sudo /etc/init.d/apache2 restart

gauthier cevin # sudo /etc/init.d/apache2 restart
apache2: Syntax error on line 237 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

Can some body give help please.

---

### Post by ooseven on 2013-03-04
This is what it says in my webmin:
[h=3]Failed to apply changes : 
apache2: Syntax error on line 237 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory Action 'configtest' failed. The Apache error log may have more information. 

Can some one direct me to how to's to set up 
[/h][TABLE="class: ui_table"]
[TR]
[TD]**Create a New Virtual Server**[/TD]
[/TR]
  [TR="class: ui_table_body"]
 [TD="colspan: 1"][TABLE="width: 100%"]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Handle connections to address**[/TD]
 [TD="class: ui_form_value, colspan: 1"] Those not handled by another server
  Any address
  Specific address ..  
 Add name virtual server address (if needed) 
 Listen on address (if needed) [/TD]
 [/TR]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Port**[/TD]
 [TD="class: ui_form_value, colspan: 1"] Default   Any     [/TD]
 [/TR]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Document Root**[/TD]
 [TD="class: ui_form_value, colspan: 1"]  
 Allow access to this directory [/TD]
 [/TR]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Server Name**[/TD]
 [TD="class: ui_form_value, colspan: 1"] Automatic       [/TD]
 [/TR]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Add virtual server to file**[/TD]
 [TD="class: ui_form_value, colspan: 1"] Standard httpd.conf file
  New file under virtual servers directory /etc/apache2/sites-available
  Selected file..    [/TD]
 [/TR]
 [TR="class: ui_form_pair"]
 [TD="class: ui_form_label"]**Copy directives from**[/TD]
 [TD="class: ui_form_value, colspan: 1"]  
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[h=3]
[/h]

---

### Post by sffvba[e0rt on 2013-03-04
*Posts moved to own thread in **General Help**.*


404

---

