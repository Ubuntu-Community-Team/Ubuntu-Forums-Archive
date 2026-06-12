---
title: "update failed"
date: 2013-12-19
forum: General Help
---

### Post by jason13 on 2013-12-19
So for the past week or so my updates have been failing to complete. the gui method failed so i tried the terminal and it still fails. I think it has something to do with a kernel version update. Here's the important part of the output of ```
sudo apt-get update
``` ```
Err http://packages.medibuntu.org precise/free amd64 Packages                    Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org precise/non-free amd64 Packages              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Err http://packages.medibuntu.org precise/free i386 Packages                   
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Err http://packages.medibuntu.org precise/non-free i386 Packages               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Err http://packages.medibuntu.org precise/free Translation-en_US               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org precise/free Translation-en                  
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Err http://packages.medibuntu.org precise/non-free Translation-en_US           
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Err http://packages.medibuntu.org precise/non-free Translation-en              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en_US            
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en               
Fetched 3,790 kB in 15s (250 kB/s)                                             
W: Failed to fetch http://packages.medibuntu.org/dists/precise/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by claracc on 2013-12-19
Medibuntu project is dead. The repositories has been moved out of the server. So you have to remove medibuntu repositories from your sources.list file.

Here, [http://askubuntu.com/questions/356998/something-wicked-happened-resolving-medibuntu-repository-what-happens](http://askubuntu.com/questions/356998/something-wicked-happened-resolving-medibuntu-repository-what-happens) you have a link explaining the issue and addressing the way you can remove medibuntu repositories.

---

