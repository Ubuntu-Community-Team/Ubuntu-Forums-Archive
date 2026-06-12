---
title: "web program for FTP transfers"
date: 2008-02-05
forum: General Help
---

### Post by jakev383 on 2008-02-05
I have several users that upload files via FTP. I have Apache set up to give a directory listing of the FTP dir so that others can download the files without having to even know what a FTP program is.
Here lies the rub.
The people who need to upload the files are, well, rather compu-tards.  They have trouble understanding why they need a FTP program when Internet Explorer is by MS and does everything. The FTP must be broke.
Anyway, they need to upload files of varying sizes. I'd like a web-based program (doesn't necessarily have to be free) that would allow them to upload files from a web app. Due to the size of some files (500M) PHP is probably out of the question unless you know how to work around the file upload size limitations (I do not, but that doesn't mean there isn't a solution).
Does anyone know of an app that will run under Apache do allow them to upload files in this manner? It doesn't have to display files, since I am already doing that with Apache. 
Thanks in advance.

---

### Post by johncudd on 2008-02-05
Yeah you can write a simple little PHP script to handle uploads. It is all web based so any idiot can upload files with any web browser. You can also put file size limitations on the uploads. Ha I hope you know PHP, and a little something about websites. By the sounds of it you already do though so you shouldn't have too much of a problem. Here is a tutorial on how to get the upload script up and working. [http://www.w3schools.com/php/php_file_upload.asp]("http://www.w3schools.com/php/php_file_upload.asp")   Let me know if you have trouble I can certainly help you out. Oh and it works fine on apache, as long as you have php installed. You can find the php addon for apache right within Synaptic.

---

### Post by cdenley on 2008-02-05
I use [uber uploader]("http://uber-uploader.sourceforge.net/"). HTTP uploading is supposed to be better with perl, which is what uber uploader users for the actual uploading. If your users upload large files, and you don't have a javascript progress bar, they will think something is wrong when the page confirming the file has uploaded takes an hour to load.

PHP can upload large files if you set the limits correctly for apache and php. Here is the .htaccess file I have used that seems to work for files up to 500MB.
```

php_value upload_max_filesize 500M
php_value post_max_size 501M
php_value max_execution_time 86400
php_value max_input_time 86400

```

---

### Post by johncudd on 2008-02-05
Man that Uber Upload is Sweet. That is definitely handy for large files.

---

### Post by jakev383 on 2008-02-05
Thanks for the replies. I'll have to look at that Uber Uploader some more. Looks like a nice package.
Thanks!

---

### Post by PinkFloyd102489 on 2008-02-05
J-FTP is a good alternative.

---

