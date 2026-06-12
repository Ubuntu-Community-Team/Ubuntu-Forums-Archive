---
title: "PHP maximum execution time exceeded after upgrade to 22.04"
date: 2023-08-30
forum: General Help
---

### Post by Petr_Be on 2023-08-30
Hello,

we are using a web application built on Nette 2.4. It was running previously on Ubuntu 18.04 with PHP 7.0. After upgrade to Ubuntu 22.04, we still use PHP 7.0 for this application because of compatibility with some of its modules. One of the features of the application is generating a CSV file from data in the database. The CSV file is then offered for download to the user.

This worked fine in Ubuntu 18.04. However, in Ubuntu 22.04 the file is not offered for download. A new browser tab is opened which is loading for cca 30 seconds, then the loading stops and the tab remains empty. The CSV file is still generated in the app's temp folder under /var/www/feudal/temp but it has to be manually copied from there. The Nette-based app's exception.log has a bunch of errors like this:

[2023-08-14 11-56-19] Fatal Error: Maximum execution time of 30 seconds  exceeded in  /var/www/feudal/vendor/nette/application/src/Application/Responses/FileResponse.php:126   @  [http://89.102.21.10:33380/feudal/history/?dateFrom=-24+hodin](http://89.102.21.10:33380/feudal/history/?dateFrom=-24+hodin)  @@  exception--2023-08-07--13-16--a40cb4bcec.html
[2023-08-14 13-36-55] Fatal Error: Maximum execution time of 30 seconds  exceeded in /var/www/feudal/vendor/tracy/tracy/src/Tracy/Helpers.php:132   @  [http://localhost/feudal/history/?dateFrom=2023-08-10+13%3A35&dateTo=2023-08-14+13%3A36&accounts[0]=1]("http://localhost/feudal/history/?dateFrom=2023-08-10+13%3A35&dateTo=2023-08-14+13%3A36&accounts%5B0%5D=1")  @@  exception--2023-08-14--13-36--e741ca4d16.html

This only started happening after upgrade from 18.04 to 22.04 with PHP remaining at 7.0 - so it shouldn't be a PHP version issue. Searching for this problem on PHP and Nette forums yielded no relevant results, so I am now trying to approach this on the OS level. Do you have any experience with this? How should I look for the cause of the problem?

Thank you very much

bhy

---

### Post by SeijiSensei on 2023-08-30
```
 /var/www/feudal/vendor/nette/application/src/Application/Responses/FileResponse.php:126
```

Have you looked at line 126 in that file? What is it trying to do? 

I've gotten maximum execution time errors when I run an iterative process that doesn't end properly. Writing out a file could have that sort of problem, one where the code doesn't realize that all the records have been processed.

I know nothing about "Nette". I just write my own PHP code in a text editor.

---

### Post by Petr_Be on 2023-08-31
Thank you. The block of code with the problematic line is as follows:

```
[FONT=monospace][COLOR=#ffff54]
    125 [/COLOR][COLOR=#000000]                $httpResponse->setHeader('Content-Length', $length); [/COLOR]
[COLOR=#ffff54]    126 [/COLOR][COLOR=#000000]                while (!feof($handle) && $length > 0) { [/COLOR]
[COLOR=#ffff54]    127 [/COLOR][COLOR=#000000]                        echo $s = fread($handle, min(4e6, $length)); [/COLOR]
[COLOR=#ffff54]    128 [/COLOR][COLOR=#000000]                        $length -= strlen($s); [/COLOR]
[COLOR=#ffff54]    129 [/COLOR][COLOR=#000000]                } [/COLOR]
[COLOR=#ffff54]    130 [/COLOR][COLOR=#000000]                fclose($handle);[/COLOR]
[/FONT]
```
which is followed by two closing brackets and the end of the file.
I guess the problem could be in there. (No idea why it worked on 18.04, though.)

---

### Post by Petr_Be on 2023-08-31
I just noticed that in Nette 2.4.10 (Nette is a PHP framework like Symfony, btw) the notation of the number on line 127 is changed:

```
 [FONT=monospace][COLOR=#000000]echo $s = fread($handle, min(4000000, $length));
[/COLOR][/FONT]
```

could this be the thing? I'll try and report back..

---

### Post by Petr_Be on 2023-08-31
So it is more complicated than that. For some reason, the value of $length is zero which results in an infinite loop. If i check the value and only run the loop when the $length is not zero (which never happens) the CSV file is indeed offered for download, but is empty. The correct file is still generated in /var/www/feudal/temp - no idea why this worked correctly on 18.04.

---

### Post by Petr_Be on 2023-08-31
Turns out it was a permissions issue after all - apache couldn't read the temporary files (hence the $length was zero), adding www-data to the mysql group (mysql being the creator and owner of the temporary files) solved the problem. Ha! Thanks again.

---

