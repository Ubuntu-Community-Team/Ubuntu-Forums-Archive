---
title: "How to securely allow a PHP script to save files?"
date: 2020-12-12
forum: General Help
---

### Post by forumate on 2020-12-12
I have a PHP script that is supposed to save files to **`/var/www/backend/files/`** folder.
The script is in **`/var/www/html/save_file.php`**


The owner and the group of all the folders and files in **`/var/www/`** is **`ubuntu`**. (And not **`www-data` -** I think that's because I'm using AWS EC2 and it configures **`ubuntu`**)


For testing, this is my simple script that won't work:


[PHP]$myfile = fopen("newfile.txt", "w") or die("Unable to open file!");
$txt = "John Doe\n";
fwrite($myfile, $txt);
$txt = "Jane Doe\n";
fwrite($myfile, $txt);
fclose($myfile);[/PHP]

And I get the following message:


> Warning: fopen(newfile.txt): failed to open stream: Permission denied in /var/www/html/save_file.php on line 2
 Unable to open file!


How can I allow this script to save files?

---

### Post by pqwoerituytrueiwoq on 2020-12-12
if newfile.txt will always exist you can [FONT=courier new]chown ubuntu:www-data[/FONT] and [FONT=courier new]chmod 664[/FONT] the file, however if you need to make new files on the fly you will need to make a dedicated folder for them
for example you can make a config folder and chmod that to like you would do the file

you may want to prevent browser access to the config folder, use a .htaccess file in the config folder
[FONT=courier new]echo Deny from all > config/.htaccess[/FONT]

---

### Post by SeijiSensei on 2020-12-12
Since Apache runs as user www-data, it has those permissions when you save files.  I suggest putting the "ubuntu" user into the www-data group and giving that group permission to write into the directory like this.
```

sudo chgrp www-data /var/www/backend/files/
sudo chmod a-w -R /var/www/backend/files/
sudo chmod g+w /var/www/backend/files/

```
I would also consider using the [fopen()]("https://www.php.net/manual/en/function.fopen.php") command in PHP to save the file as read-only:
```

$filename='something.txt';
$fp=fopen("/path/to/some/directory/$filename","r");

```

---

