---
title: "EyeOS 1.9.0.3-1 on Ubuntu 16.04"
date: 2017-09-07
forum: General Help
---

### Post by trueeasy on 2017-09-07
[COLOR=#333333][FONT=Ubuntu]Hey Guys, I am currently studying in a Introductory Linux course.Our professor has given us an Assignment to install EyeOS on Ubuntu 16.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Steps I have done:[/FONT][/COLOR]

[LIST]
[*]Install Ubuntu 16.04 on Virtualbox
[*]Install lamp server (dependencies for EyeOS)```
sudo apt-get install lamp-server^
```
[*]Download eyeOS 1.9.0.3-1.zip [here]("https://www.mediafire.com/file/p0nd8ahd84jd3un/eyeOS_1.9.0.3-1.zip")
[*]Change to Download folder ```
cd /home/'username'/Downloads
```
[*]move the zip file to html folder ```
mv eyeOS_1.9.0.3-1.zip /var/www/html
```
[*]change to html direcotry ```
cd /var/www/html/
```
[*]unzip file ```
unzip eyeOS_1.9.0.3-1.zip
```
[*]change directory eyeOS ```
cd eyeOS
```
[*]change permissions ```
chmod 777 ./index.html
``````
chmod 777 ./
``` ```
chmod 777 ./installer/
``` ```
chmod 777./package.eyepackage
```
[*]Install sqlite3```
sudo spt-get install sqlite3
```
[*]Install php imap ```
sudo apt-get install php7.0-imap
```
[*]restart apache```
service apache2 restart
```
[*]Open page ```
localhost/eyeOS/installer
```
[/LIST]
[COLOR=#333333][FONT=Ubuntu][https://imgur.com/da36pew](https://imgur.com/da36pew)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I am facing the issue shown in the screenshot[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Any help would be greatly appreciated![/FONT][/COLOR]

---

### Post by btindie on 2017-09-08
Have you read the error message? Your're missing the mbstring and sqlite3 php modules
```

sudo apt-get install php7.0-mbstring php7.0-sqlite3

```

---

