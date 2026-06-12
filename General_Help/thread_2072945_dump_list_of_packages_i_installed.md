---
title: "dump list of packages i installed"
date: 2012-10-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-18
is there a way i can get a list of packages i install excluding auto installed dependencies (anything that could be removed with apt-get autoremove)

---

### Post by Lisiano on 2012-10-18
Install [Synaptic](apt://synaptic). It's an awesome frontend. You may find manually installed packages in Status -> Installed (manual). Though I don't know how to get a dump from it.

---

### Post by pqwoerituytrueiwoq on 2012-10-18
synaptic is one of the 1st things i install, thanks *goes to look at list*

---

### Post by jerrrys on 2012-10-18
Do you mean just your installed app's?  With out the depend's ..

/usr/share/applications

---

### Post by cmcanulty on 2012-10-18
in synaptic go to file-save markings as and check save full state not just changes name it and save it somewhere

---

### Post by pqwoerituytrueiwoq on 2012-10-18
@cmcanulty
that appears to be the same as dpkg --get-selections
lets say i install the libreoffice metapackage
this installs all the parts i need and if i remove the meta package autoremove would get rid of the rest of libreoffice
i basically want a list of everything i installed without dependencies
@[jerrrys]("http://ubuntuforums.org/member.php?u=718079")
i want it to include command line utilities like tree

if a package is installed because it is a dependency and you installed the package it was installed for and you run *apt-get autoremove *it will ask to remove the other pacakge
but if i run *apt-get install [insert installed dependency here]* autoremove will no longer try to take that package out
i want a list of everything that is not auto-removable, is there a way i can sun a sql select query on the database?

---

### Post by oldfred on 2012-10-18
I normally use dpkg to list all my installed apps. 

Someone posted that from aptitude you an get the top level without dependencies. I do not know if you an do that from dpkg or not.

Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install

Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'
sudo aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' >toplevelonly

---

### Post by pqwoerituytrueiwoq on 2012-10-18
thanks that should get the job done

---

### Post by pbrane on 2012-10-18
Another way to get the installed debs from your system is
```

dpkg --get-selections | grep -v deinstall > installed-debs

```
this will create a file called installed-debs with everything you have installed.

---

### Post by pqwoerituytrueiwoq on 2012-10-18
that includes dependencies...
i am going to use the top level one above and run a php script through it to compare it to a list made on a clean install to only have the ones i installed
i will post the script when i make it tomorrow
not today i have a headache
edit:
the file toplevel comes from ```
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > ~/toplevel
```
the file ~/stock-toplevel comes from this being run on a clean install
```
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > ~/stock-toplevel
```
[PHP]#!/usr/bin/php5
<?php 
$full=explode("\n",file_get_contents("~/toplevel"));
$empty=explode("\n",file_get_contents("~/stock-toplevel"));
$new=Array();
for($i=0;$i<count($full);$i++){
	if($full[$i] == 'playdeb' || $full[$i] == 'getdeb-repository')
		continue;
	if(! in_array($full[$i],$empty))
		array_push($new,$full[$i]);
}
echo "#!/bin/sh\nsudo apt-get install ".implode(" ",$new);
?>
[/PHP]

---

