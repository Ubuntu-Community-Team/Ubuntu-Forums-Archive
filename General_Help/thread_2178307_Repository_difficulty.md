---
title: "Repository difficulty"
date: 2013-10-02
forum: General Help
---

### Post by Claude_Sutton on 2013-10-02
I have recently reinstalled 12.04 and I am having a lot of problems with the repositorys.

I get "badsig" messages.  Hash marks not the same. etc.

Not able to ....whatever...xxx repository.

I am having a particular problem getting vim properly downloaded and installed.  I get the missing message on some critical file.

Is this a common problem with the latest version of 12.04?

What to do?

---

### Post by Bashing-om on 2013-10-02
Claude_Sutton; Hi ! Welcome to the forum .

No, that is not a common issue. For assistance in your issue, post back to us the command you are using and the exact error message that is generated. Could be the result of several causes.

Place that out put between code tags.
Tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT][INDENT]where there are solutions there is no problem
[/INDENT][/INDENT][/INDENT]

---

### Post by Claude_Sutton on 2013-10-02
This is what I just got when asking synaptic to download vim.

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.3.429-2ubuntu2.1_amd64.deb
  Hash Sum mismatch
```

I am using all of the depositories in synaptic, both ubuntu and others.

---

### Post by Bashing-om on 2013-10-02
Claude_Sutton; Hey.

could be your /lists file is messed up .. but let's look at this first>
show:
```

apt-cache policy vim
apt-get update
apt-get upgrade

```

Just to ensure the foundation is solid to work from.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Claude_Sutton on 2013-10-02
```
claude@claude-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get update
[sudo] password for claude: 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:5 http://us.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://archive.canonical.com precise Release.gpg                           
Get:6 http://extras.ubuntu.com precise Release.gpg [72 B]            
Hit http://us.archive.ubuntu.com precise Release                               
Ign http://us.archive.ubuntu.com precise Release                               
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release                               
Get:8 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Err http://us.archive.ubuntu.com precise-updates Release                       
  
Get:9 http://us.archive.ubuntu.com precise-proposed Release [49.6 kB]          
Ign http://us.archive.ubuntu.com precise-backports Release                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://us.archive.ubuntu.com precise/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com precise/restricted Sources/DiffIndex          
Err http://us.archive.ubuntu.com precise-proposed Release                      
  
Ign http://us.archive.ubuntu.com precise/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com precise/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com precise/main amd64 Packages/DiffIndex         
Ign http://us.archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com precise/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex
Hit http://extras.ubuntu.com precise/main amd64 Packages              
Get:10 http://security.ubuntu.com precise-security/main Sources [89.6 kB]
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com precise/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com precise/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://us.archive.ubuntu.com precise/universe TranslationIndex             
100% [10 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitin
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign http://us.archive.ubuntu.com precise-backports/main Sources/DiffIndex      
Ign http://us.archive.ubuntu.com precise-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-backports/universe i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages.IndexDiff - open (2: No such file or directory)
claude@claude-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
claude@claude-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get -tvv update
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]       
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:4 http://us.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise Release                                   
Hit http://us.archive.ubuntu.com precise Release                               
Ign http://us.archive.ubuntu.com precise Release                               
Hit http://archive.canonical.com precise Release                               
Get:5 http://security.ubuntu.com precise-security/main Sources [89.6 kB]       
100% [5 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:6 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Err http://us.archive.ubuntu.com precise-updates Release                       
  
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:8 http://security.ubuntu.com precise-security/universe Sources [28.1 kB]   
Ign http://us.archive.ubuntu.com precise-backports Release                     
Ign http://us.archive.ubuntu.com precise-proposed Release                      
Ign http://us.archive.ubuntu.com precise/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com precise/restricted Sources/DiffIndex          
Ign http://us.archive.ubuntu.com precise/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com precise/multiverse Sources/DiffIndex          
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://us.archive.ubuntu.com precise/main amd64 Packages/DiffIndex         
Ign http://us.archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com precise/universe amd64 Packages/DiffIndex     
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,804 B] 
Get:10 http://security.ubuntu.com precise-security/main amd64 Packages [324 kB]
Ign http://us.archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com precise/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com precise/universe i386 Packages/DiffIndex      
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex    
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages.IndexDiff (1)

claude@claude-HP-Pavilion-dv7-Notebook-PC:~$ 

```

---

### Post by Yellow Pasque on 2013-10-02
Go through the steps, and if it still doesn't work after Step 5, post the output from all of the commands (again, use code tags because it will be a lot of text).
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by Claude_Sutton on 2013-10-02
It worked.  I really appreciate the help.  I never would have found that on my own.  Thank you.

---

### Post by Claude_Sutton on 2013-10-02
It has been so long since I have posted here that I forgot how to mark this thread as solved.

---

### Post by Bashing-om on 2013-10-02
Claude_Sutton;
Did not intend to abandon you .. system problems happen to the best of us!

Glad ya got it resolved !

To mark the thread as solved .. go to your 1st post, -> thread tools.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

