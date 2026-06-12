---
title: "apt-get problem in ubuntu 10.04"
date: 2014-09-01
forum: General Help
---

### Post by mrityunjay23 on 2014-09-01
**I am using ubuntu 10.04. I want setting in my system such that I can use apt-get download and other like wget..etc downloads as well. **
Smilie which are appearing they are :p

Initially, I have put  /etc/apt/apt.conf file following line. Acquire::http:proxy "http://username\:password@proxyhost:port/";
Then my apt-get was working. 

**I was wanted to download some dropbox software from website. I have put following line in ~/.bashrc file**
http_proxy="http://username:password@proxy_server_address:port_no"
export http_proxy
**and then I have removed apt.conf Acquire entry.** 

**1. When I type source ~/.bashrc it gives following error.**
bash: export: `[http://username:password@proxy_server_address:port_no':](http://username:password@proxy_server_address:port_no':) not a valid identifier

**2. When I do apt-get update, I get following error**
```

Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main Translation-en_IN            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/multiverse Translation-en_IN    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_IN              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Packages                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Packages             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Packages
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Error!
W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing multimedia-soundsynthesis (NewFileDesc2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
```

**3. When I do wget "www.google.co.in" then I get**

--2014-09-01 17:01:58--  [http://www.google.co.in/](http://www.google.co.in/)
Connecting to 202.141.80.80:3128... connected.
Proxy request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [ <=>                                   ] 20,109      --.-K/s   in 0.1s    

2014-09-01 17:01:58 (198 KB/s) - `index.html.1' saved [20109]
I think my wget is working. [B]

How to check that apt-get and other download like wget..etc are working?

I am getting confused with file modification please clarify me which file I must modify ~/.bashrc or apt.conf. I want to use all downloadable facilities.
[/B]

---

### Post by sudodus on 2014-09-01
Ubuntu Server 10.04 LTS should work, but Ubuntu (Desktop) 10.04 LTS passed end of life in April 2013 (more than one year ago) and the desktop packages are no longer updated. This can cause failures like the one you have now, and it makes the desktop system vulnerable to attacks via the internet. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

So the first question is:

- Are you running the Ubuntu Server or Ubuntu Desktop?

With a multimedia-soundsynthesis problem mentioned in your 'sudo apt-get update' output list, I guess it is a desktop installation. If that is the case I strongly suggest that you save all your personal files and install a current version of Ubuntu: 12.04.5 LTS or 14.04.1 LTS, or some other flavour of Ubuntu, if the computer is too old for standard Ubuntu: Lubuntu 14.04.1 LTS or Xubuntu 14.04.1 LTS. 

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL]
If you are running the Ubuntu Server, we'll look closer into your problem and try to solve it.

---

### Post by coffeecat on 2014-09-01
Not a Tutorial, so..

*Thread moved to **General Help**.*

If you wish to avoid accidental smileys in your post, use the advanced message editor and tick the "disable smileys" box below the text editor before posting.

By the way, I notice you have Saucy (13.10) sources in your apt-get output as well as Lucid (10.04). 13.10 is also end-of-life now. With mixed sources like that, your system could well give you insoluble dependency problems. Bearing in mind what sudodus mentioned, that the desktop version of 10.04 is end of life now, you would be well advised making a fresh install of a supported version such as 14.04.

---

