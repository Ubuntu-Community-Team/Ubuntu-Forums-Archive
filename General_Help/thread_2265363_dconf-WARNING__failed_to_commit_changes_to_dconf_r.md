---
title: "dconf-WARNING **: failed to commit changes to dconf: refused connection"
date: 2015-02-14
forum: General Help
---

### Post by faustf on 2015-02-14
hi  guy 
i have  a  problem :D
so ,  i have  created a script in python , this  script  change a wallpaper ,  i try to insert in crontab ,  but    have  always  this  error 

```
(process:25190): dconf-CRITICAL **: unable to create file '/home/stefano/.cache/dconf/user': Permesso negato.  dconf will not work properly.

(process:25190): dconf-WARNING **: failed to commit changes to dconf: Impossibile connettersi: Connessione rifiutata
```

this  is   a line  for  crontab 

```
* * * * * export DISPLAY=:0.0 && export XAUTHORITY=/home/stefano/.Xauthority && sudo -u stefano /usr/bin/python /home/stefano/Documenti/PROGRAMMAZIONE/python/script_ok/bingbong_ubuntu_unity  2> /tmp/erro$


```

and  this  is  a python program 

```
#!/usr/bin/python#-------------------------------------------------------------------------------------------------------------
#*    program =  BINGBONG , wallpaper by bing (nice pics)
#*    Author = Cerbioni Stefano 
#*    mail = info@e-officecom.com 
#*    version number 1.0 
#-------------------------------------------------------------------------------------------------------------
import urllib
import re
import os
import urllib2


#from urllib.request import urlopen
SITO="http://www.bing.com"
sock = urllib2.urlopen(SITO) 
htmlSource = sock.read() 
sock.close()


searchObj = re.search( r'(.*)\{url\:\'(.*?) .*', htmlSource, re.M|re.I)


if searchObj:
   # Delete Python-style comments
        num = re.sub(r'\\', "",  searchObj.group(2))  #rimuove i back slash
        num2 = re.sub(r'\,', "",  num)                        #rimuove le virgole
        num3 = re.sub(r'\'', "", num2)                       # rimuove apice  
        DOWN=SITO+num3                                            # crea indirizzo da scaricare
        response = urllib2.urlopen(DOWN)
        nomefile= re.sub(r'\/az\/hprichbg\/rb\/', "", num3)
        # print "Phone Num : ", nomefile
#open the file for writing
output = open('/usr/share/backgrounds/'+nomefile,'wb')
output.write(response.read())
output.close()


os.system("gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/"+nomefile)







```

some one  ,  have  some idea   for  wich reason dont  go?? :)

in  lubuntu 14  go perfect  but  in ubuntu 14  no :(

---

