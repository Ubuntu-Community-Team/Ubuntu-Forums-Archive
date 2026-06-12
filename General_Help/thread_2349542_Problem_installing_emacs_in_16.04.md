---
title: "Problem installing emacs in 16.04"
date: 2017-01-15
forum: General Help
---

### Post by skippylou on 2017-01-15
Trying to install emacs 24.5 + sbcl 1.3.6 (x64) + quicklisp + slime on ubuntu 16.04 (x64) using this procedure:

[http://let-over-lambda-p.blogspot.com/2015/08/ubuntu-15.html](http://let-over-lambda-p.blogspot.com/2015/08/ubuntu-15.html)

The second step is :

sudo apt-get build-dep emacs24

to which I get the reply:

Reading package lists... Done
E: You must put some 'source' URIs in your sources.list

I found a suggestion here: [http://askubuntu.com/questions/826890/apt-build-dep-fails-unable-to-locate-source-package-despite-deb-src-lines-pres](http://askubuntu.com/questions/826890/apt-build-dep-fails-unable-to-locate-source-package-despite-deb-src-lines-pres)  to un-comment deb-src lines in the file /etc/apt/sources.list.  I un-commented all 11 lines beginning "deb-src" and I get the same error message.

History of this installation of 16.04 (not 16.04.1) on a clean HD:

1.  Installed Nvidia driver using the ppa:graphics-drivers archive.  All is OK.

2.  Installed google-chrome-stable.  The installation works fine but now I get a red circle with a minus sign on the top of desktop toolbar.  Followed instructions which it leads to but it doesn't go away.

3.  Purged all ppa archives.  Strange error message went away.  

4.  Proceeded to try to install emacs as described above.

Since I it is very early in my configuration of this system I am not opposed to starting over from scratch, maybe with 16.04.1.
I thought about uncommenting EVERYTHING in /etc/apt/sources.list but this would be a WASITD.

Thanks for any suggestions.

PS Did all of the Ubuntu updates ans also ran:

sudo apt install build-essential checkinstall

---

### Post by &amp;KyT$0P# on 2017-01-16
Did you run
```
sudo apt-get update
```
after un-commenting those sources.list lines?

---

### Post by skippylou on 2017-01-16
> **halogen2 said:**
> Did you run
```
sudo apt-get update
```
after un-commenting those sources.list lines?

OK, thanks, but I get a box on the screen:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;                                                                         &#9474; 
  &#9474; Please select the mail server configuration type that best meets your     
  &#9474; needs.                                                                    
  &#9474;                                                                           
  &#9474;  No configuration:                                                        
  &#9474;   Should be chosen to leave the current configuration unchanged.          
  &#9474;  Internet site:                                                           
  &#9474;   Mail is sent and received directly using SMTP.                          
  &#9474;  Internet with smarthost:                                                 
  &#9474;   Mail is received directly using SMTP or by running a utility such       
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                  
  &#9474;  Satellite system:                                                        
  &#9474;   All mail is sent to another machine, called a 'smarthost', for          
  &#9474; delivery.                                                                 
  &#9474;  Local only:                                                              
  &#9474;                                                                           
  &#9474;                                 <Ok>                                      
  &#9474;                                                                         &#9474; 
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

And I have no clue as to how to make this selection or exit to the terminal command line.

??????????????????/

> **skippylou said:**
> OK, thanks, but I get a box on the screen:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;                                                                         &#9474; 
  &#9474; Please select the mail server configuration type that best meets your     
  &#9474; needs.                                                                    
  &#9474;                                                                           
  &#9474;  No configuration:                                                        
  &#9474;   Should be chosen to leave the current configuration unchanged.          
  &#9474;  Internet site:                                                           
  &#9474;   Mail is sent and received directly using SMTP.                          
  &#9474;  Internet with smarthost:                                                 
  &#9474;   Mail is received directly using SMTP or by running a utility such       
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                  
  &#9474;  Satellite system:                                                        
  &#9474;   All mail is sent to another machine, called a 'smarthost', for          
  &#9474; delivery.                                                                 
  &#9474;  Local only:                                                              
  &#9474;                                                                           
  &#9474;                                 <Ok>                                      
  &#9474;                                                                         &#9474; 
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

And I have no clue as to how to make this selection or exit to the terminal command line.

??????????????????/

Hit Esc and get this box: &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                                              &#9474; General type of mail configuration:  &#9474; 
                                              &#9474;                                      &#9474; 
                                              &#9474;       No configuration               &#9474; 
                                              &#9474;       Internet Site                  &#9474; 
                                              &#9474;       Internet with smarthost        &#9474; 
                                              &#9474;       Satellite system               &#9474; 
                                              &#9474;       Local only                     &#9474; 
                                              &#9474;                                      &#9474; 
                                              &#9474;                                      &#9474; 
                                              &#9474;       <Ok>           <Cancel>        &#9474; 
                                              &#9474;                                      &#9474; 
                                              &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

Up and down arrows allow me to select which configuration.  "Enter" just returns me to the first box.  What next?

---

### Post by &amp;KyT$0P# on 2017-01-17
At that box, does Tab key do anything?

---

