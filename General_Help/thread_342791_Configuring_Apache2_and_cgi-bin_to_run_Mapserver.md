---
title: "Configuring Apache2 and cgi-bin to run Mapserver"
date: 2007-01-20
forum: General Help
---

### Post by GISuser on 2007-01-20
Folks,

I am new to Linux, Ubuntu, Apache2, and Mapserver and need help with the proper location of the cgi-bin folder and folders that Apache2 and Mapserver needs to access.  I am running Apache2 (v. 2.0.55), Mapserver (v. 4.8.3-2), and Ubuntu 6.10.  Apache2 and Mapserver is running and working.

Below is a brief history of the installation procedure.  Following the history is a question on the cgi-bin folder location and where to place html documents and sample data for Mapserver.

My goal is to run an FTP and a map server.  My first priority is the map server.  I am running Ubuntu 6.10.

I installed Apache2 and Mapserver (downloading the libraries suggested in the UbuntuGIS docuement) using Synaptic.  I also downloaded libraries as suggested in the document located at [URL="http://translate.google.com/translate?hl=en&sl=fr&u=http://www.geotests.net/cours/mapserver/mapserverUbuntu.txt&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dmapserv%2Bubuntu%26start%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DMtN%26sa%3DN."]http://translate.google.com/translate?hl=en&sl=fr&u=http://www.geotests.net/cours/mapserver/mapserverUbuntu.txt&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dmapserv%2Bubuntu%26start%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DMtN%26sa%3DN.
[/URL]
Sorry for the long URL, I used google translation to translate the page from French to English.

I am also using the installation guidelines listed in two books: 1) "Beggining MapServer: Open Source GIS Developement" by apress and 2) "Web Mapping Illustrated" by O'Reilly. The guidelines are specific to Linux Slackware.   I will then test Mapserver using the demo data in the books.    

What I know (thanks to the forums!):

Apache2 default cgi-bin location: /usr/lib/cgi-bin
Apache2 default user and group name: www-data
Synaptic placed the mapserver executable "mapserv" in /usr/lib/cgi-bin.

***_QUESTIONS FOLLOW:_***


[LIST=1]
[*]  The books suggest copying mapserv to "/var/www/cgi-bin/".  But the default location for cgi-bin is "/usr/lib/cgi-bin/" for my Apache2 installation.  Do I need to chage the default location or can I just change the code in the sample *.html and *.map files?  If I need to change the location of the cgi-bin folder, please advise me how to do this.  Currently, there is no cgi-bin folder in "/var/www/"

[*] The books suggest creating two folders.  One folder accessible to Mapserver and the other folder accessible to Apache2 and Mapserver.  

First Folder:  the text suggestes placing spatial data in the /home/ directory and making the folder accessible to Mapserver as follows:
```
mkdir /home/mapdata/
chown nobody:nobody /home/mapdata/
chmod u+rx /home/mapdata/
```

I plan on modifying the above code to: 
```
# mkdir /home/mapdata/
# chown www-data:www-data /home/mapdata
# chmod u+rx /home/mapdata/

```

Will this code work in Ubuntu 6.10?
I will be putting sample data into the folder mapdata later.

Second Folder:  the text suggestes creating a folder where Mapserver can save images to a file by performing the following to make a folder accessible to Apache2 and Mapserver:
```
mkdir /var/www/htdocs/tmp
chown nobody:nobody /var/www/htdocs/tmp
chmod u+rx /var/www/htdocs/tmp
```

I plan modifying the code to:
```
# mkdir /var/www/apache2-default/tmp
# chown www-data:www-data /var/www/apache2-default/tmp
# chmod u+rx /var/www/apache2-default/tmp
```

Note:  I am assuming the folder /apache2-default/ is equivelent to /htdocs/ used in the book.

Will this work?


[*]  Where do I put my index.html file that is accessible by the localhost and ulitmately the internet?  In "/var/www/apache2-default/" or "/var/www/"?
[/LIST]

Thank you very much, in advanced, for your input.

---

