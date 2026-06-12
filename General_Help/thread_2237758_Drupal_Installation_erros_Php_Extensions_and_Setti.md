---
title: "Drupal Installation erros: Php Extensions and Settings file"
date: 2014-07-25
forum: General Help
---

### Post by olamide2 on 2014-07-25
Good day everyone

                           We are trying to install Drupal 7 on ubuntu 12.04 but we are stucked at a point. Following an handout **"http://tinyurl.com/8e428c9"** we got to a point called Upload Progress and ran this command "pecl install uploadprogress" which worked well. After these we tried running  the command

"echo "extension = uploadprogress.so" > /etc/php5/apache2/conf.d/php.ini " 

but the response we got says :

"bash: /etc/php5/apache2/conf.d/php.ini: Permission denied"

We ve been unable to move beyond this point. Can we please get some help. 



Olamide

---

### Post by steeldriver on 2014-07-25
You will need to use 'sudo' to gain the necessary authority to write to the file

```

sudo sh -c 'echo "extension = uploadprogress.so" > /etc/php5/apache2/conf.d/php.ini'

```
or
```

echo "extension = uploadprogress.so" | sudo tee /etc/php5/apache2/conf.d/php.ini

```
or
```

sudo -i
echo "extension = uploadprogress.so" > /etc/php5/apache2/conf.d/php.ini
exit

```

---

### Post by olamide2 on 2014-07-30
Thank you so much [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500") it worked.....however after a sucessful installation we tried to launch drupal but we couldnt get it. We restarted apache using the command sudo service apache2 restart it worked after which we tried 127.0.1.1/drupal but it wouldnt work. Please what can we do. Thanks.

---

### Post by steeldriver on 2014-07-30
I don't see anything in the instructions you linked that actually installs drupal... it just sets up LAMP **for** drupal

---

### Post by olamide2 on 2014-08-01
Awww thanks, [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG] realised that and we finally installed drupal via [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal) and was sucessful however while in the finall installation process we got to the verify requirements field and we got to error messages:


[TABLE="class: system-status-report"]
[TR="class: error merge-down"]
[TD="class: status-icon"]1)
[/TD]
[TD="class: status-title"]PHP extensions[/TD]
[TD="class: status-value"]Disabled[/TD]
[/TR]
[TR="class: error merge-up"]
[TD="class: status-description, colspan: 3"]Drupal requires you to enable the PHP extensions in the following list (see the [system requirements page]("http://drupal.org/requirements") for more information):
[LIST]
[*]gd 
[/LIST]
[/TD]
[/TR]
[/TABLE]

[TABLE="class: system-status-report"]
[TR="class: error merge-down"]
[TD="class: status-title"]2) Settings file[/TD]
[TD="class: status-value"]The settings file is not writable.[/TD]
[/TR]
[TR="class: error merge-up"]
[TD="class: status-description, colspan: 3"]The Drupal installer requires write permissions to *./sites/default/settings.php* during the installation process. If you are unsure how to grant file permissions, consult the [online handbook]("http://drupal.org/server-permissions").


Please how do we resolve it. Thanks for the assistance.
[/TD]
[/TR]
[/TABLE]

---

### Post by olamide2 on 2014-08-03
[**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG] realised that and we finally installed drupal via [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)  and was sucessful however while in the finall installation process we  got to the verify requirements field and it gave us error messages:


[TABLE="class: cms_table_system-status-report"]
[TR="class: cms_table_error cms_table_merge-down"]
[TD="class: cms_table_status-icon"]1)[/TD]
 [TD="class: cms_table_status-title"]PHP extensions[/TD]
 [TD="class: cms_table_status-value"]Disabled[/TD]
 [/TR]
 [TR="class: cms_table_error cms_table_merge-up"]
[TD="class: cms_table_status-description, colspan: 3"]Drupal requires you to enable the PHP extensions in the following list (see the [system requirements page]("http://drupal.org/requirements") for more information):

[LIST]
[*]gd
[/LIST]
[/TD]
 [/TR]
 [/TABLE]

 
[TABLE="class: cms_table_system-status-report"]
[TR="class: cms_table_error cms_table_merge-down"]
[TD="class: cms_table_status-title"]2) Settings file[/TD]
 [TD="class: cms_table_status-value"]The settings file is not writable.[/TD]
 [/TR]
 [TR="class: cms_table_error cms_table_merge-up"]
[TD="class: cms_table_status-description, colspan: 3"]The Drupal installer requires write permissions to *./sites/default/settings.php* during the installation process. If you are unsure how to grant file permissions, consult the [online handbook]("http://drupal.org/server-permissions").


Please how do we resolve it. Thanks for the assistance.[/TD]
[/TR]
[/TABLE]

---

### Post by olamide2 on 2014-08-03
**[COLOR=#C61919]WE [/COLOR]**realised that and we finally installed drupal via [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)  and was sucessful however while in the finall installation process we  got to the verify requirements field and it gave us error messages:


[TABLE="class: cms_table_system-status-report"]
[TR="class: px&quot;cms_table_error"]
[TD="class: cms_table_status-title cms_table_system-status-report cms_table_error cms_table_merge-down"]2) Settings file[/TD]
 [TD="class: cms_table_status-value cms_table_system-status-report cms_table_error cms_table_merge-down"]The settings file is not writable.[/TD]
 [/TR]
 [TR="class: cms_table_error cms_table_merge-up cms_table_system-status-report"]
[TD="class: cms_table_status-description, colspan: 3"]The Drupal installer requires write permissions to *./sites/default/settings.php* during the installation process. If you are unsure how to grant file permissions, consult the [online handbook]("http://drupal.org/server-permissions").


Please how do we resolve it. Thanks for the assistance.[/TD]
[/TR]
[/TABLE]

---

### Post by steeldriver on 2014-08-03
well I have zero experience with drupal, but my guesses would be 

1) you need to install the php5-gd package

2) probably doesn't mean anything more than that you need to run the installer with 'sudo' (which presumably you are doing anyway)

---

### Post by olamide2 on 2014-08-03
[**[COLOR=#C61919][B]Please we **[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")realised that and we finally installed drupal via [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)  and was sucessful however while in the finall installation process we  got to the verify requirements field and it gave us error messages:


[TABLE="class: cms_table_system-status-report"]
[TR]
[TD="class: cms_table_status-title cms_table_error cms_table_merge-down"]2) Settings file[/TD]
[TD="class: cms_table_status-value cms_table_error cms_table_merge-down"]The settings file is not writable.[/TD]
[/TR]
[TR="class: cms_table_error cms_table_merge-up"]
[TD="class: cms_table_status-description, colspan: 3"]The Drupal installer requires write permissions to *./sites/default/settings.php* during the installation process. If you are unsure how to grant file permissions, consult the [online handbook]("http://drupal.org/server-permissions").


Please how do we resolve it. Thanks for the assistance.[/TD]
[/TR]
[/TABLE]

---

### Post by steeldriver on 2014-08-03
Threads merged - please don't start multiple threads on the same topic, if you feel your thread is in the wrong forum you can report it requesting for it to be moved

---

### Post by olamide2 on 2014-08-04
Am sorry about the multiple threads...

---

