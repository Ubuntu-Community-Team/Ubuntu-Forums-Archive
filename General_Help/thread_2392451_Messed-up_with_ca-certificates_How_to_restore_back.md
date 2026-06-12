---
title: "Messed-up with ca-certificates/ How to restore back to default"
date: 2018-05-21
forum: General Help
---

### Post by yathomasi on 2018-05-21
Recently I tried to add own ssl for ```
https
``` support in localhost which I couldn't achieve but now i am getting all these error with certificates




I am getting error updating with certificates error ```
sudo apt update
```


    ```
Hit:1 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) bionic InRelease
    Hit:2 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                                                                    
    Hit:3 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                                                                  
    Hit:4 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) bionic-proposed InRelease                                                                                   
    Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                                                                           
    Ign:6 [https://deb.nodesource.com/node_8.x](https://deb.nodesource.com/node_8.x) bionic InRelease                                                                                            
    Ign:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                          
    Get:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease [10.2 kB]                                                                                  
    Hit:9 [http://ppa.launchpad.net/hluk/copyq/ubuntu](http://ppa.launchpad.net/hluk/copyq/ubuntu) bionic InRelease                                                                                     
    Ign:10 [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) cloud-sdk-bionic InRelease                                                                               
    Hit:11 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                           
    Err:12 [https://deb.nodesource.com/node_8.x](https://deb.nodesource.com/node_8.x) bionic Release                                                                                             
      Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 13.33.170.36 443]
    Hit:13 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease                                                                                    
    Err:14 [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) cloud-sdk-bionic Release                                                                                 
      Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 74.125.68.113 443]
    Ign:15 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ InRelease                                                                                         
    Hit:16 [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu) bionic InRelease                                                 
    Ign:17 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                                                                       
    Hit:18 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                                                                             
    Hit:19 [http://ppa.launchpad.net/ubuntubudgie/backports/ubuntu](http://ppa.launchpad.net/ubuntubudgie/backports/ubuntu) bionic InRelease                                                   
    Err:20 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Release                                                
      Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.236.0.104 443]
    Reading package lists... Done                                                        
    W: [https://deb.nodesource.com/node_8.x/dists/bionic/InRelease:](https://deb.nodesource.com/node_8.x/dists/bionic/InRelease:) No system certificates available. Try installing ca-certificates.
    W: [https://packages.cloud.google.com/apt/dists/cloud-sdk-bionic/InRelease:](https://packages.cloud.google.com/apt/dists/cloud-sdk-bionic/InRelease:) No system certificates available. Try installing ca-certificates.
    W: [https://deb.nodesource.com/node_8.x/dists/bionic/Release:](https://deb.nodesource.com/node_8.x/dists/bionic/Release:) No system certificates available. Try installing ca-certificates.
    W: [https://download.sublimetext.com/apt/stable/InRelease:](https://download.sublimetext.com/apt/stable/InRelease:) No system certificates available. Try installing ca-certificates.
    E: The repository 'https://deb.nodesource.com/node_8.x bionic Release' no longer has a Release file.
    N: Updating from such a repository can't be done securely, and is therefore disabled by default.
    N: See apt-secure(8) manpage for repository creation and user configuration details.
    W: [https://packages.cloud.google.com/apt/dists/cloud-sdk-bionic/Release:](https://packages.cloud.google.com/apt/dists/cloud-sdk-bionic/Release:) No system certificates available. Try installing ca-certificates.
    E: The repository 'https://packages.cloud.google.com/apt cloud-sdk-bionic Release' no longer has a Release file.
    N: Updating from such a repository can't be done securely, and is therefore disabled by default.
    N: See apt-secure(8) manpage for repository creation and user configuration details.
    W: [https://download.sublimetext.com/apt/stable/Release:](https://download.sublimetext.com/apt/stable/Release:) No system certificates available. Try installing ca-certificates.
    E: The repository 'https://download.sublimetext.com apt/stable/ Release' no longer has a Release file.
    N: Updating from such a repository can't be done securely, and is therefore disabled by default.
    N: See apt-secure(8) manpage for repository creation and user configuration details.
```


Also while at ```
git push
```


    ```
fatal: unable to access 'https://github.com/username/project.git/': server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

```

```
cat /etc/ssl/certs/ca-certificates.crt
```  is blank.

---

### Post by TheFu on 2018-05-21
Just put that file back.   Use your last backup.

---

