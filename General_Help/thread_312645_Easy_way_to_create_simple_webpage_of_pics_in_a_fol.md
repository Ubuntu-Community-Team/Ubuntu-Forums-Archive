---
title: "Easy way to create simple webpage of pics in a folder?"
date: 2006-12-04
forum: General Help
---

### Post by kvonb on 2006-12-04
I run a very simple webserver (webFS) and would like to create a very basic page showing thumbnails of all the images in a given folder.  It would be nice if it was dynamic, ie updated when I added new images but running a script each time I add new images is fine.  Anyone have suggestions?

Thanks, KEv :)

---

### Post by strabes on 2006-12-04
Do you have PHP installed on your server? You could use a PHP script to read a directory with all the images in it, and then generate the html code using variables for the url. I think this should work. It's a pretty basic php script. I took it from one of the old websites I designed a looong time ago. If it does work, it would generate a bunch of thumbnails 100x100 in size which link to the real image.

<php>
$path = "images/pics/yourdirectory"; 

$dir_handle = @opendir($path) or die("Unable to open $path"); 

while ($file = readdir($dir_handle)) { 

if(!is_dir($file)) { 

$filesize = filesize($path.$file); 

echo "<a href=$path$file target=_blank><img src=$file height=100 width=100 /></a>"; 

} 

} 

closedir($dir_handle); 


<php>

---

### Post by Greguti on 2006-12-04
Hello,

try the "web album" function (Tools menu) inside GThumb. It's quite easy to set up and very quick. Look at [http://www.greguti.com/petitlinux/albumtest](http://www.greguti.com/petitlinux/albumtest) for an example.

GThumb is installed with your Ubuntu OS. 

Regards

Greg

---

### Post by kvonb on 2006-12-04
Excellent suggestions, I will try both of them later :).

Thankyou very much :)

---

### Post by sam81 on 2006-12-04
Have a look at igal [http://nanoheat.stanford.edu/epop/igal/]("http://nanoheat.stanford.edu/epop/igal/"), you can install it from the repos.

Cheers

---

### Post by kvonb on 2006-12-04
Thanks Sam81, Igal works a treat.

Check this out:

[http://wamrfixit.homeip.net:8000/edgy/screenshots/](http://wamrfixit.homeip.net:8000/edgy/screenshots/)

Unfortunately GThumb uses CSS and is too advanced for the very simple WebFS server and wouldn't work and I am too lazy to install and get PHP running :D

Thanks all!

---

### Post by strabes on 2006-12-04
That's ok :)

---

### Post by wgscott on 2006-12-04
[Jalbum](http://jalbum.net/download3.jsp)

---

