---
title: "How to restore default path to executable"
date: 2014-02-18
forum: General Help
---

### Post by Doug S on 2014-02-18
Hi,

Due to incompetence on my part, I find myself trying to recover from a bit of a mess I created for default paths to executable programs of a package. Instead of looking for the executable in its normal default location, the system seems to be looking for it in another location that was temporarily used for a test version of the package. Here is what happens now:```
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help/C$ [COLOR=#ff0000]yelp-check validate *.page[/COLOR]
-bash: /usr/local/bin/yelp-check: No such file or directory
```The program "yelp-check" is part of the package "yelp-tools", and previously I had built and installed a new version directly from the GNOME git. However, I made a mistake with the package name, calling it "yelp" by mistake (which did not create yet another issue, because my build computer is a server, without "yelp" normally installed). You can see from the package contents, the package had "yelp-check" at the above location:```
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help/C$ [COLOR=#ff0000]dpkg --contents /home/doug/temp-yelp-git/yelp-tools/yelp_3.11.0-1_amd64.deb[/COLOR]
drwxr-xr-x root/root         0 2014-01-16 13:56 ./
drwxr-xr-x root/root         0 2012-03-21 08:32 ./usr/
drwxr-xr-x root/root         0 2012-03-14 08:42 ./usr/local/
drwxr-xr-x root/root         0 2014-01-16 13:56 ./usr/local/bin/
-rwxr-xr-x root/root     24250 2014-01-16 13:56 [COLOR=#ff0000]./usr/local/bin/yelp-check[/COLOR]
-rwxr-xr-x root/root     20473 2014-01-16 13:56 ./usr/local/bin/yelp-build
-rwxr-xr-x root/root      4412 2014-01-16 13:56 ./usr/local/bin/yelp-new
drwxr-xr-x root/root         0 2014-01-16 13:46 ./usr/local/share/
drwxr-xr-x root/root         0 2014-01-16 13:56 ./usr/local/share/aclocal/
... a bunch deleted ...
-rw-rw-r-- root/root        33 2014-01-16 10:37 ./usr/share/doc/yelp/AUTHORS
``` I have uninstalled the test package and even uninstalled and re-installed the default "yelp-tools" package from the repos. I can manually make the command work by forcing the entire path:```
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help/C$ [COLOR=#ff0000]time /usr/bin/yelp-check validate *.page[/COLOR]

real    0m7.196s
user    0m0.920s
sys     0m0.688s
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help/C$
```However, I want the default to work again. Does anybody have any suggestions?
By the way, my path is:```
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help/C$ [COLOR=#ff0000]echo $PATH[/COLOR]
/home/doug/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:[COLOR=#ff0000]/usr/bin[/COLOR]:/sbin:/bin:/usr/games
```And the computer is an Ubuntu 12.04 server. Also, I have since learned how to get my test .deb files to have the right package name and to put files to the right locations.

---

### Post by Doug S on 2014-02-18
> **Doug S said:**
> Also, I have since learned how to get my test .deb files to have the right package name and to put files to the right locations.Of course, therein was the answer to my problem. By recompiling the .deb, but keeping the wrong package name and fixing the file install locations, I was able to fix however it was pointing to the wrong location. I had to:
[LIST]
[*]Uninstall yelp-tools, to prevent dpkg from getting upset with overlaying files from what it thought was another package (because of my naming mistake). 
[*]Install my newly built .deb package with the files locations correct. 
[*]Uninstall my newly built .deb package. 
[*]Install the default yelp-tools using "sudo apt-get install yelp-tools" 
[/LIST]
I am not yet setting this post to "SOLVED" because I am still wondering if there was an easier, or better, way to fix up the mess I created.

---

### Post by fdrake on 2014-02-18
have you tried re-declaring it?
```
echo "export PATH=/home/doug/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games" >> ~/.bashrc
```

logout/in

---

### Post by Doug S on 2014-02-18
@fdrake: Thanks for your reply.

I'm setting this to solved because now I can not recreate the issue to test other suggestions. I can only guess that I had some other compounding factor messed up, but it got sorted out.

---

