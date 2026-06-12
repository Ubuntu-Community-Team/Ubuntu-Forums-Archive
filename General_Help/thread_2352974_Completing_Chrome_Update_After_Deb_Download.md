---
title: "Completing Chrome Update After Deb Download"
date: 2017-02-17
forum: General Help
---

### Post by ozark_hillbilly on 2017-02-17
I have been getting a repeated notification from Google that my Chrome browser is not up to date. So I downloaded the latest deb file (google-chrome-stable 56.0.2924.87) and then extracted the files. I noticed that the extraction simply put the new deb folders in the Downloads folder. I assumed it would put them where they needed to be properly located/stored. I was wrong evidently to assume that.
What is the most straightforward way to accomplish the update? Software center, Terminal mode, or what? I am currently operating under Chrome Version 48.0.2564.103 and using Ubuntu 14.04.5 LTS.
There may be a sticky or post that explains all this but I haven't see it.

I realize this is probably a no brainer for most Linux users but I rarely go into the "guts" of Ubuntu/Linux as it so wonderfully stable and I have no reason to fix what isn't broken.

Thanks Folks!

---

### Post by Impavidus on 2017-02-17
Double clicking on the .deb file in the file manager should be sufficient. Don't extract it. Else, you can use the terminal:```
sudo dpkg --install path/to/file.deb
```
But chrome is supposed to put google's server into your software sources, so chrome should update automatically along with your other software. Maybe there's something wrong with that? I assume you have a 64 bit system, don't you?

---

### Post by deadflowr on 2017-02-17
You shouldn't have needed to download a fresh copy.
Chrome should update through Ubuntu update system.

That said, you can either simply double click on chrome and the software center should open allowing you to install it that way, or
use dpkg or apt to install the deb
```
sudo dpkg -i /full/path/to/deb/file.deb
```
this method has a quirk in which it does not satisfy dependencies issues 
(however if you already had chrome installed, thos dependency issues should already be resolved)
but in case there are issues, you would run
```
sudo apt-get install -f
```
and that will resolve those issues.

[s]the other command that should work (even on 14.04)
is
```
sudo apt install /full/path/to/deb-file.deb
```
this method does resolve those pesky dependency issues.[/s]
ignore that, it does not work on 14.04.

Once installed, though, chrome will get updates as part of the overall updates that your system gets.
If for some reason you are not getting updates for chrome or other programs, then there may be something amiss about your update configuration.
you can run
```
sudo apt update
```
to see if the connections to the repos is functional. Or if something is erring out
and
```
sudo apt upgrade
```
to install any updates.

Or run the Software Updater program.
(it, too, will show errors if any exists)

---

### Post by Autodave on 2017-02-17
You could also install *gdebi* (in the repositories) and use that to install the file that you downloaded.

---

### Post by ozark_hillbilly on 2017-02-18
howdy deadflowr,

I went in terminal and executed the sudo apt update and upgrade with no errors. When I tried to do the sudo apt install it says the deb was not found. ???
Looking at the Terminal screenshot below you can see the file in my Downloads folder but the process is not seeing it for some unknown reason.

Any ideas why that is? 
Dazed and confused,
Ed

 ed@ed-G41MT-S2PT:~/Downloads$ dir

google-chrome-stable_current_amd64.deb                    			                                      


ed@ed-G41MT-S2PT:~/Downloads$ sudo apt install /home/ed/Downloads/google-chrome-stable_current_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package /home/ed/Downloads
ed@ed-G41MT-S2PT:~/Downloads$

---

### Post by uNoubu8a on 2017-02-18
> **Autodave said:**
> You could also install *gdebi* (in the repositories) and use that to install the file that you downloaded.

I also normally use gdebi and haven't used apt to install a local file.

```
sudo apt install gdebi
sudo gdebi /home/ed/Downloads/google-chrome-stable_current_amd64.deb
```

Perhaps you can try the above?

---

### Post by deadflowr on 2017-02-18
> **ozark_hillbilly said:**
> howdy deadflowr,

I went in terminal and executed the sudo apt update and upgrade with no errors. When I tried to do the sudo apt install it says the deb was not found. ???
Looking at the Terminal screenshot below you can see the file in my Downloads folder but the process is not seeing it for some unknown reason.

Any ideas why that is? 
Dazed and confused,
Ed

 ed@ed-G41MT-S2PT:~/Downloads$ dir

google-chrome-stable_current_amd64.deb                    			                                      


ed@ed-G41MT-S2PT:~/Downloads$ sudo apt install /home/ed/Downloads/google-chrome-stable_current_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package /home/ed/Downloads
ed@ed-G41MT-S2PT:~/Downloads$

Yeah, I see that command does not work as such on 14.04.
Thought it did at one time.
So scratch that idea.

But aside from that you do have several other ways to install it.
And also, since you had chrome installed already, maybe see if running
```
sudo apt-get install google-chrome-stable
```
does, since chrome adds it's own repository, which if you did not remove, would still be accessible.

---

### Post by RobGoss on 2017-02-19
You should be able to update Google chrome right from the Chrome browser, I don't see the update buttom because I already have the latest version, take a look at this help page from Google chrome [https://support.google.com/chrome/answer/95414?co=GENIE.Platform%3DDesktop&hl=en](https://support.google.com/chrome/answer/95414?co=GENIE.Platform%3DDesktop&hl=en)

---

### Post by howefield on 2017-02-19
> **ozark_hillbilly said:**
> I have been getting a repeated notification from Google that my Chrome browser is not up to date. So I downloaded the latest deb file (google-chrome-stable 56.0.2924.87) and then extracted the files. I noticed that the extraction simply put the new deb folders in the Downloads folder. I assumed it would put them where they needed to be properly located/stored. I was wrong evidently to assume that.
What is the most straightforward way to accomplish the update? Software center, Terminal mode, or what? I am currently operating under Chrome Version 48.0.2564.103 and using Ubuntu 14.04.5 LTS.
There may be a sticky or post that explains all this but I haven't see it.

I realize this is probably a no brainer for most Linux users but I rarely go into the "guts" of Ubuntu/Linux as it so wonderfully stable and I have no reason to fix what isn't broken.

Thanks Folks!

As others have said, Chrome should put some repository sources details into your /etc/apt/sources.list.d/ folder whereby the normal update process would take of updating your Chrome browser.

Have you checked to see that you do have such a repository and on the assumption that you have, try from the terminal

```
sudo apt update
```
```
sudo apt upgrade
```

Sorry : ignore - missed in the thread that you had already tried that.

---

### Post by ozark_hillbilly on 2017-02-21
Man, this is getting to be a big bummer. Trying all suggestions, including loading unsuccessfully off web through Google Chrome site, but no luck so far. Ran upgrade installation, going to ver 53.02.785.143, under SPK (Syn Pkg Mgr) but the upgrade process would never finish. In fact, it's still running in the other window stuck in a loop (?). Here's the screenshot attachment and if anyone has *any* ideas I'm all ears. This an annoying problem but as long as my ver 48 (old I know) of Chrome is functioning it's not the end of the world.Hippy Ed.

P.S. I don't wan't to delete the current version and reload unless I know I can save the proper files that will retain my bookmarks & config data.

---

### Post by howefield on 2017-02-22
> **ozark_hillbilly said:**
> ... but the upgrade process would never finish. In fact, it's still running in the other window stuck in a loop (?). 

Hard to see the text in the image but looks to be stuck on installing chromium-browser, however there is an issue with that [package and Trusty]("https://ubuntuforums.org/showthread.php?t=2352049&highlight=chromium+browser+trusty").

Chrome being based on Chromium may be have the same problem.

---

### Post by vasa1 on 2017-02-22
> **howefield said:**
> Hard to see the text in the image but looks to be stuck on installing chromium-browser, however there is an issue with that [package and Trusty]("https://ubuntuforums.org/showthread.php?t=2352049&highlight=chromium+browser+trusty").

Chrome being based on Chromium may be have the same problem.

I think OP is trying to update chromium-browser and _not_ google-chrome-stable. Hence the problem :( 

I haven't come across issues updating google-chrome on 14.04 systems.

OP, please post the output of```
apt-cache policy chromium-browser google-chrome*
```

---

### Post by ozark_hillbilly on 2017-02-23
Hi vasa1,

Here is requested dump:

```
ed@ed-G41MT-S2PT:~$ apt-cache policy chromium-browser google-chrome*
chromium-browser:
  Installed: 53.0.2785.143-0ubuntu0.14.04.1.1145
  Candidate: 53.0.2785.143-0ubuntu0.14.04.1.1145
  Version table:
 *** 53.0.2785.143-0ubuntu0.14.04.1.1145 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages
        500 [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) trusty-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     34.0.1847.116-0ubuntu2 0
        500 [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) trusty/universe i386 Packages
google-chrome-stable:
  Installed: 48.0.2564.103-1
  Candidate: 48.0.2564.103-1
  Version table:
 *** 48.0.2564.103-1 0
        100 /var/lib/dpkg/status
ed@ed-G41MT-S2PT:~$ 
```

Attached is screenshot of Google Chrome About.

Thanks for any suggestions on problem.

---

### Post by vasa1 on 2017-02-23
Support for 32-bit Google Chrome is no longer available:
[http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)
[http://askubuntu.com/questions/763298/where-can-you-download-32-bit-edition-of-google-chrome-for-ubuntu-os](http://askubuntu.com/questions/763298/where-can-you-download-32-bit-edition-of-google-chrome-for-ubuntu-os)
[http://unix.stackexchange.com/questions/267587/where-to-download-chrome-32bit-since-it-has-been-discontinued-by-google](http://unix.stackexchange.com/questions/267587/where-to-download-chrome-32bit-since-it-has-been-discontinued-by-google)

---

### Post by ozark_hillbilly on 2017-03-11
No solution available evidently. Thread abandoned.

---

