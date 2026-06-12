---
title: "404 Errors"
date: 2013-10-17
forum: General Help
---

### Post by Chelidze on 2013-10-17
Just installed ubuntu 13.10 
I did apt-update in terminal and sow this 

```
Err http://ppa.launchpad.net /ubuntu/saucy amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net /ubuntu/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net /ubuntu/saucy i386 Packages  
  404  Not Found
Err http://ppa.laun

```

```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/saucy/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/saucy/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

I do not understand why am I getting this errors wine's ppa shows that 13.10 is available and the above I even do not know what is it ?? any help how to fix this

---

### Post by Frogs Hair on 2013-10-17
If the PPA has  been updated for 13.10  try again later   . The maintainers tend to wait until the final image is released to ensure compatibility . PPA's are not official packages and you can disable the source in Software & Updates > Other Software until the PPA is available again to get rid of the error.

---

### Post by Chelidze on 2013-10-17
> **Frogs Hair said:**
> If the PPA has  been updated for 13.10  try again later   . The maintainers tend to wait until the final image is released to ensure compatibility . PPA's are not official packages and you can disable the source in Software & Updates > Other Software until the PPA is available again to get rid of the error.
Thank you for the reply sure -->ubuntu-wine/ppa is something that I understand and can remove knowing what it will cause however this 
```
[COLOR=#000000][FONT=Ubuntu Mono]Err http://ppa.launchpad.net /ubuntu/saucy amd64 Packages                       [/FONT][/COLOR]  404  Not Found
Err http://ppa.launchpad.net /ubuntu/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net /ubuntu/saucy i386 Packages  
  404  Not Found [COLOR=#000000][FONT=Ubuntu Mono]Err http://ppa.laun[/FONT][/COLOR]
```
what is it ?? and they will enable it ?? or I should as you mentioned just wait

---

### Post by Frogs Hair on 2013-10-17
I am connecting to that source when I run the sudo apt-get update , so it may be a server glitch . How long have you had the errors ?

---

### Post by Chelidze on 2013-10-17
> **Frogs Hair said:**
> I am connecting to that source when I run the sudo apt-get update , so it may be a server glitch . How long have you had the errors ?

I just did a clean install of 13.10 and when I did an update and saw the error I posted it right away on the forum should I reinstall ??

I really do not get this and please some one help me with this ok I understand that wine ppa got messed up some how even though I followed this guide 
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)
it always worked for me but not know 
this [person]("http://askubuntu.com/a/360562/42591") on askubuntu helped me fix it 

> [COLOR=#333333][FONT=UbuntuRegular]The repository isn't added properly to the APT sources. Have you been editing the ```
sources.list
``` file manually? Please don't do that![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]As you can see APT now tries to fetch[/FONT][/COLOR]
```
http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-i386/Packages 

```[COLOR=#333333][FONT=UbuntuRegular]instead of (correct):[/FONT][/COLOR]
```
http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/saucy/main/binary-i386/Packages

```[COLOR=#333333][FONT=UbuntuRegular]Please use the ```
add-apt-repository
``` utility next time to add PPAs. I suggest to remove the repository from your ```
sources.list
``` for now and re-add the repository:[/FONT][/COLOR]
```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa_-saucy.list
sudo add-apt-repository ppa:ubuntu-wine/ppa

```[COLOR=#333333][FONT=UbuntuRegular]Then run[/FONT][/COLOR]
```
sudo apt-get update

```[COLOR=#333333][FONT=UbuntuRegular]again and it should use a working URL.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
it fixed my problem but I have a question how did it fix the first 404 error 

```
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Err http://ppa.launchpad.net /ubuntu/saucy amd64 Packages                       [/FONT][/COLOR]
  404  Not Found
Err http://ppa.launchpad.net /ubuntu/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net /ubuntu/saucy i386 Packages  
  404  Not Found [COLOR=#000000][FONT=Ubuntu Mono]Err http://ppa.laun[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
```

Was it connected to wine or it got [/FONT][/COLOR]resolved by itself and just timing was on spot

---

### Post by Frogs Hair on 2013-10-17
I don't have Wine installed I just noticed the source in the terminal output when running update. I wouldn't reinstall, but wait for more input from others.    

```
Hit http://ppa.launchpad.net saucy/main amd64 Packages  
```

---

