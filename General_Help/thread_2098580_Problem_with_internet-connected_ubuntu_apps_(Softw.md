---
title: "Problem with internet-connected ubuntu apps (Software Center, Nuvola Player, Lightrea"
date: 2012-12-27
forum: General Help
---

### Post by Ubun 2 on 2012-12-27
There seems to be something broken with the Ubuntu Software  Center (or at least my install of it), and what ever it is also effects  some other internet-connected native ubuntu apps (Software Center, Ubuntu Tweak, Nuvola  Player, and Lightread (although lightread doesn't give the error  message)).

  When I try to install a free app that goes through the payment  service (as in one that you 'buy' for $0.00), or a paid app, in the  Software Center, I get this message:

  *Unable to load page Problem occurred while loading the URL [https://software-center.ubuntu.com/subscriptions/en/ubuntu/quantal/+new/?archive_id=commercial-ppa-uploaders%2Fstormcloud&arch=amd64](https://software-center.ubuntu.com/subscriptions/en/ubuntu/quantal/+new/?archive_id=commercial-ppa-uploaders%2Fstormcloud&arch=amd64) Cannot resolve hostname (software-center.ubuntu.com)*

  Nuvola gives me a similar message:

  *Unable to load page Problem occurred while loading the URL [http://8tracks.com/](http://8tracks.com/) Cannot resolve hostname (8tracks.com)*

  And Ubuntu Tweak gives:

  *Unable to load page Problem occurred while loading the URL [http://ubuntu-tweak.com/utapp/](http://ubuntu-tweak.com/utapp/) Cannot resolve hostname (ubuntu-tweak.com)*

  I have tried reinstalling everything other than the Software Center.  The problem appeared a few weeks ago. My internet works fine. I have  screenshots of the errors but I don't think it would help much; they  just look like an unstyled firefox Server Not Found error, and have a  'try again button'. 

  I have no clue what is wrong,  and any help would be greatly appreciated!
Ubun 2

---

### Post by Ubun 2 on 2012-12-30
Does anyone know what package handles the internet connection for these apps? Any ideas?

---

### Post by ibjsb4 on 2012-12-30
Hi Ubun2, welcome to the forums  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the output.

---

### Post by Ubun 2 on 2013-01-01
Thanks for your reply. I get:

```
myusername@Ubun2:~$ sudo apt-get update
[sudo] password for myusername: 
Ign http://extras.ubuntu.com quantal InRelease
Ign http://security.ubuntu.com quantal-security InRelease                      
Ign http://archive.canonical.com quantal InRelease                             
Ign http://ca.archive.ubuntu.com quantal InRelease                             
Ign http://ppa.launchpad.net quantal InRelease                                 
Get:1 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://archive.canonical.com quantal Release.gpg                           
Ign http://ca.archive.ubuntu.com quantal-updates InRelease                     
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://archive.canonical.com quantal Release                               
Ign http://ca.archive.ubuntu.com quantal-backports InRelease                   
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://ca.archive.ubuntu.com quantal Release.gpg                           
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://archive.canonical.com quantal/partner Sources                       
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com quantal-updates Release.gpg                   
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Get:2 http://ca.archive.ubuntu.com quantal-backports Release.gpg [933 B]       
Ign https://private-ppa.launchpad.net quantal InRelease                        
Hit http://security.ubuntu.com quantal-security/universe Sources               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://ca.archive.ubuntu.com quantal Release                               
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://ca.archive.ubuntu.com quantal-updates Release                       
Hit http://security.ubuntu.com quantal-security/main amd64 Packages            
Ign http://ppa.launchpad.net quantal InRelease                                 
Get:3 http://ca.archive.ubuntu.com quantal-backports Release [49.6 kB]         
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages      
Ign https://private-ppa.launchpad.net quantal InRelease                        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages      
Hit http://ca.archive.ubuntu.com quantal/main Sources                          
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Hit http://ca.archive.ubuntu.com quantal/restricted Sources                    
Ign https://private-ppa.launchpad.net quantal InRelease                        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com quantal/universe Sources                      
Ign http://extras.ubuntu.com quantal/main Translation-en_CA                    
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://ca.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages
Ign http://archive.canonical.com quantal/partner Translation-en_CA    
Hit http://ca.archive.ubuntu.com quantal/main amd64 Packages          
Hit http://ppa.launchpad.net quantal Release.gpg                      
Ign http://archive.canonical.com quantal/partner Translation-en       
Hit http://ca.archive.ubuntu.com quantal/restricted amd64 Packages    
Ign https://private-ppa.launchpad.net quantal InRelease               
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit http://security.ubuntu.com quantal-security/main Translation-en   
Hit http://ca.archive.ubuntu.com quantal/universe amd64 Packages
Hit http://ppa.launchpad.net quantal Release.gpg
Hit http://ca.archive.ubuntu.com quantal/multiverse amd64 Packages
Hit http://ppa.launchpad.net quantal Release.gpg
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com quantal/main i386 Packages
Hit http://ppa.launchpad.net quantal Release.gpg
Hit https://private-ppa.launchpad.net quantal Release.gpg
Hit http://ca.archive.ubuntu.com quantal/restricted i386 Packages     
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit https://private-ppa.launchpad.net quantal Release.gpg
Hit http://ca.archive.ubuntu.com quantal/universe i386 Packages       
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit https://private-ppa.launchpad.net quantal Release.gpg             
Hit http://ca.archive.ubuntu.com quantal/multiverse i386 Packages     
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit https://private-ppa.launchpad.net quantal Release.gpg
Hit http://ca.archive.ubuntu.com quantal/main Translation-en_CA       
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit https://private-ppa.launchpad.net quantal Release
Hit http://ca.archive.ubuntu.com quantal/main Translation-en                   
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit https://private-ppa.launchpad.net quantal Release
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit https://private-ppa.launchpad.net quantal Release                 
Hit http://ca.archive.ubuntu.com quantal/multiverse Translation-en     
Hit http://ppa.launchpad.net quantal Release                          
Hit https://private-ppa.launchpad.net quantal Release                          
Hit http://ppa.launchpad.net quantal Release                           
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Hit http://ca.archive.ubuntu.com quantal/restricted Translation-en    
Hit http://ppa.launchpad.net quantal Release                          
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en_CA   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en               
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/main Sources                  
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Sources            
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/universe Sources              
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Sources            
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/main amd64 Packages           
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://security.ubuntu.com quantal-security/main Translation-en_CA         
Hit http://ca.archive.ubuntu.com quantal-updates/restricted amd64 Packages     
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_CA   
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Hit http://ca.archive.ubuntu.com quantal-updates/universe amd64 Packages       
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_CA   
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse amd64 Packages     
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ca.archive.ubuntu.com quantal-updates/main i386 Packages            
Ign http://security.ubuntu.com quantal-security/universe Translation-en_CA     
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ca.archive.ubuntu.com quantal-updates/restricted i386 Packages      
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com quantal-updates/universe i386 Packages        
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse i386 Packages      
Hit http://ca.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com quantal-updates/universe Translation-en       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:4 http://ca.archive.ubuntu.com quantal-backports/main Sources [14 B]       
Get:5 http://ca.archive.ubuntu.com quantal-backports/restricted Sources [14 B] 
Get:6 http://ca.archive.ubuntu.com quantal-backports/universe Sources [5,185 B]
Hit http://ppa.launchpad.net quantal/main Sources                              
Get:7 http://ca.archive.ubuntu.com quantal-backports/multiverse Sources [781 B]
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Get:8 http://ca.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Get:9 http://ca.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:10 http://ca.archive.ubuntu.com quantal-backports/universe amd64 Packages [4,748 B]
Get:11 http://ca.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [1,118 B]
Hit http://ppa.launchpad.net quantal/main Sources                              
Get:12 http://ca.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Get:13 http://ca.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:14 http://ca.archive.ubuntu.com quantal-backports/universe i386 Packages [5,567 B]
Get:15 http://ca.archive.ubuntu.com quantal-backports/multiverse i386 Packages [1,118 B]
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ca.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:16 http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en [594 B]
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com quantal-backports/universe Translation-en     
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Ign http://ca.archive.ubuntu.com quantal/multiverse Translation-en_CA          
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Ign http://ca.archive.ubuntu.com quantal/restricted Translation-en_CA          
Ign http://ca.archive.ubuntu.com quantal-updates/main Translation-en_CA        
Ign http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en_CA  
Ign http://ca.archive.ubuntu.com quantal-updates/universe Translation-en_CA    
Ign http://ca.archive.ubuntu.com quantal-backports/main Translation-en_CA      
Ign http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/universe Translation-en_CA  
Ign https://private-ppa.launchpad.net quantal/main Translation-en_CA           
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign https://private-ppa.launchpad.net quantal/main Translation-en_CA
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign https://private-ppa.launchpad.net quantal/main Translation-en_CA
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign https://private-ppa.launchpad.net quantal/main Translation-en_CA
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Fetched 69.8 kB in 43s (1,599 B/s)
Reading package lists... Done
myusername@Ubun2:~$
```

Thanks,
Ubun2

---

### Post by ibjsb4 on 2013-01-01
Wow, quite the list you have.  Anyhow that updated your system without problem.  Is the software center still broke?  If so, once again in terminal:

```
gksudo software-center
```

Get any errors?

---

### Post by Ubun 2 on 2013-01-01
The software center still has the same problem. This is what I get when I gksudo it:

```
myusername@Ubun2:~$ gksudo software-center
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gksudo:6686): Gtk-WARNING **: Theme directory status/16 of theme NITRUX-Clear-All has no size field

2013-01-01 13:08:06,725 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-01-01 13:08:07,130 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'

(software-center:6724): Gtk-WARNING **: Theme directory status/16 of theme NITRUX-Clear-All has no size field

2013-01-01 13:08:07,190 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-01-01 13:08:07,243 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-01-01 13:08:07,246 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-01-01 13:08:09,839 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'lordofultima'' not available
2013-01-01 13:08:09,840 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'decane-rcminiracers'' not available
2013-01-01 13:08:09,840 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'plexmediaserver'' not available
2013-01-01 13:08:09,845 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-01-01 13:08:13,696 - softwarecenter.db.update - INFO - 'SCAApplicationParser'.make_doc: skipping region restricted app u'Comentarios Web' (region not whitelisted)
2013-01-01 13:08:14,187 - softwarecenter.db.update - INFO - 'SCAApplicationParser'.make_doc: skipping region restricted app u"Bulleti d'esquerra de Calonge i Sant Antoni " (region not whitelisted)
2013-01-01 13:08:15,357 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-01-01 13:08:15,357 - softwarecenter.db.database - INFO - reopen() database
2013-01-01 13:08:15,357 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
myusername@Ubun2:~$
```Most of that is the output from when I closed the software center.

Thanks for your help,
Ubun2

---

### Post by ibjsb4 on 2013-01-01
Once again this looks ok, those warnings will not shut you down.  So lets have a look at (in terminal):

```
cat -n /etc/apt/sources.list.d/*
```

and

```
cat -n /etc/apt/sources.list
```

What Im trying to do is locate those bad sources in your first post.

---

### Post by Ubun 2 on 2013-01-01
From ```
cat -n /etc/apt/sources.list.d/*
``` I get:

```
myusername@Ubun2:~$ cat -n /etc/apt/sources.list.d/*
     1    deb http://ppa.launchpad.net/alecive/antigone/ubuntu quantal main
     2    deb http://ppa.launchpad.net/cooperjona/lightread/ubuntu quantal main
     3    deb-src http://ppa.launchpad.net/cooperjona/lightread/ubuntu quantal main
     4    deb http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu quantal main
     5    deb-src http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu quantal main
     6    deb http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu quantal main
     7    deb-src http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu quantal main
     8    deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main
     9    deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main
    10    deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main
    11    deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main
    12    # deb http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu quantal main
    13    # deb-src http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu quantal main
    14    deb http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu quantal main
    15    deb-src http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu quantal main
    16    deb http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu quantal main
    17    deb-src http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu quantal main
    18    deb http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu quantal main
    19    deb-src http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu quantal main
    20    deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu quantal main
    21    deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu quantal main
    22    deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu quantal main
    23    deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu quantal main
    24    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/apollo/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    25    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/apollo/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    26    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/flareget/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    27    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/flareget/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    28    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    29    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    30    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/slimboat/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    31    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/slimboat/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
    32    deb http://ppa.launchpad.net/sparkers/ppa/ubuntu quantal main
    33    deb-src http://ppa.launchpad.net/sparkers/ppa/ubuntu quantal main
    34    deb http://ppa.launchpad.net/sparkers/ppa/ubuntu quantal main
    35    deb-src http://ppa.launchpad.net/sparkers/ppa/ubuntu quantal main
    36    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu quantal main
    37    deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu quantal main
    38    deb http://ppa.launchpad.net/tiheum/equinox/ubuntu quantal main
    39    deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu quantal main
    40    deb http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu quantal main
    41    deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu quantal main
    42    deb http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu quantal main
    43    deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu quantal main
    44    deb http://ppa.launchpad.net/webupd8team/themes/ubuntu quantal main
    45    deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu quantal main
    46    deb http://ppa.launchpad.net/webupd8team/themes/ubuntu quantal main
    47    deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu quantal main
    48    deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main
    49    deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main
    50    deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main
    51    deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu quantal main
    52    deb http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu quantal main
    53    deb-src http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu quantal main
    54    deb http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu quantal main
    55    deb-src http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu quantal main
    56    deb http://ppa.launchpad.net/yorba/ppa/ubuntu quantal main
    57    deb-src http://ppa.launchpad.net/yorba/ppa/ubuntu quantal main
    58    deb http://ppa.launchpad.net/yorba/ppa/ubuntu quantal main
    59    deb-src http://ppa.launchpad.net/yorba/ppa/ubuntu quantal main
myusername@Ubun2:~$ 

```

And ```
cat -n /etc/apt/sources.list
``` outputs:

```
myusername@Ubun2:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ca.archive.ubuntu.com/ubuntu/ quantal main restricted
     6    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
    11    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://ca.archive.ubuntu.com/ubuntu/ quantal universe
    17    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal universe
    18    deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates universe
    19    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://ca.archive.ubuntu.com/ubuntu/ quantal multiverse
    27    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal multiverse
    28    deb http://ca.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
    29    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://ca.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
    37    deb-src http://ca.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu quantal-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
    41    deb http://security.ubuntu.com/ubuntu quantal-security universe
    42    deb-src http://security.ubuntu.com/ubuntu quantal-security universe
    43    deb http://security.ubuntu.com/ubuntu quantal-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu quantal partner
    51    # deb-src http://archive.canonical.com/ubuntu quantal partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu quantal main
    56    deb-src http://extras.ubuntu.com/ubuntu quantal main
    57    deb http://archive.canonical.com/ quantal partner
    58    deb-src http://archive.canonical.com/ quantal partner
myusername@Ubun2:~$ 

```

Thanks!

---

### Post by ibjsb4 on 2013-01-02
Please stand by

---

### Post by Ubun 2 on 2013-01-03
Are you talking about editing a file? In my sources.list.d directory there is a pair of files for each ppa, one ending with '.list', and the other ending with '.save'. The contents seem to be mostly the same in both files (a deb link and a deb-src link), but some are different. Do I delete both of the files or just one?

I attached a screenshot  my sources.list.d

Thanks for your time!

---

### Post by ibjsb4 on 2013-01-04
Copy/paste/enter in terminal:

```
sudo cp -r /etc/apt/sources.list.d /etc/apt/sources.list.d.old2 && sudo rm /etc/apt/sources.list.d/alecive-antigone-quantal.list /etc/apt/sources.list.d/alecive-antigone-quantal.list.save && sudo apt-get update
```

And try the software center.

---

### Post by Ubun 2 on 2013-01-04
Still no luck. I don't use most of the software in sources.list, and I could easily get back the ones I do use, what about wholesale deleting the contents of sources.list and starting fresh if that's where the problem is?

I really appreciate your time ibjsb4.

---

### Post by ibjsb4 on 2013-01-04
> **Ubun 2 said:**
> what about wholesale deleting the contents of sources.list and starting fresh if that's where the problem is?

Ok, lets remove sources.list.d.  You have a backup (.old2).

```
sudo rm /etc/apt/sources.list.d/* && sudo apt-get update
```

And try the software center

---

### Post by Ubun 2 on 2013-01-04
I tried it with no luck. I could just wait and reinstall when 13.04 comes out, which would be a somewhat unsatisfactory solution. The package must be a dependency in all the apps that are malfunctioning -- do you know of an easy way to list the dependencies of an application?

---

### Post by ibjsb4 on 2013-01-04
> **Ubun 2 said:**
> do you know of an easy way to list the dependencies of an application?

Yes and try a different package manager at the same time.  Its called Synaptic Package Manager.  It will list all dependencies and other things with a right click and go to properties.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

```
sudo apt-get install synaptic
```

---

### Post by docmech on 2013-04-09
I started having the same problem in 12.04 after a recent update. I thought at first it was a problem with software center but now I realize it was one of the updates. I still haven't found a solution yet either. I'm following your thread and hoping.

---

### Post by docmech on 2013-04-09
Also I failed to mention that I can no longer see screenshots in appcenter as well.

---

