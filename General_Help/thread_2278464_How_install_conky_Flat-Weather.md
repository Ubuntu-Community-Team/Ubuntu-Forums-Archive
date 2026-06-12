---
title: "How install conky Flat-Weather?"
date: 2015-05-16
forum: General Help
---

### Post by esmarra on 2015-05-16
HI
1. instalei conky atraves center software ubuntu!
2. In terminal $ sudo apt-get install conky imagemagick
3. Install nautilus sudo apt-get install nautilus
4. Created folder [B].conky
[https://lh3.googleusercontent.com/-nUPDmP5cJWY/UYTS-BIq8qI/AAAAAAAAqnw/LKeS6gd-g3o/s400/flat_weather_conky_nautilus.jpg](https://lh3.googleusercontent.com/-nUPDmP5cJWY/UYTS-BIq8qI/AAAAAAAAqnw/LKeS6gd-g3o/s400/flat_weather_conky_nautilus.jpg)
[https://lh4.googleusercontent.com/-bgewoJQOEdw/UYTTkR3uv9I/AAAAAAAAqoY/sbETfvz7TUQ/s400/flat_weather_conky_menu.jpg](https://lh4.googleusercontent.com/-bgewoJQOEdw/UYTTkR3uv9I/AAAAAAAAqoY/sbETfvz7TUQ/s400/flat_weather_conky_menu.jpg)
[https://lh6.googleusercontent.com/-tYC1keKIdBg/UYTToX_E3tI/AAAAAAAAqog/l1FX73pRj-w/s756/flat_weather_conky_inicio.jpg](https://lh6.googleusercontent.com/-tYC1keKIdBg/UYTToX_E3tI/AAAAAAAAqog/l1FX73pRj-w/s756/flat_weather_conky_inicio.jpg)
[/B]Already I restarted the computer but does not appear on the desktop?
Can anyone help me ?

---

### Post by leunam12 on 2015-05-16
Make sure that conky is running open terminal and type: ```
ps -eo pid,cmd | grep conky
``` if conky is running do:```
killall conky
conky -c /home/yunn/.conky/Flat-Wheater/conkyrc
```if conky appears after you do this, you may have to delay conky a few seconds after startup. If conky does not appear but it's running you may have to change the windows type to normal and see what happens.

---

### Post by esmarra on 2015-05-16
esmarra@esmarra-HP-Compaq-6720s:~$ ps -eo pid,cmd | grep conky
 6179 conky -c /home/esmarra/.conky/Flat-Wheater/conkyrc
 6364 grep --color=auto conky




[http://i.imgur.com/aMShIYL.png](http://i.imgur.com/aMShIYL.png)

---

### Post by leunam12 on 2015-05-16
Looks like you have two problems:
1-conky is running at startup but you don't see it because it starts before your desktop wallpaper and it gets covered.
2-conky is whining about problems with the configuration file.

Here is how you may solve your first problem: create an empty document on your /home/esmarra directory and name it .conky_start.sh. Open it and paste this code inside:```
#! /bin/bash

sleep 10
conky -c /home/esmarra/.conky/Flat-Wheater/conkyrc
exit
```then open the terminal and type:```
chmod +x .conky_start.sh
```Then edit your conky startup command on your second picture on your first post instead of "conky -c /home/esmarra/.conky/Flat-Wheater/conkyrc" your startup comand should be ```
/home/esmarra/.conky_start.sh
```what that is going to do is that is going to delay conky ten seconds to give time to the desktop wallpaper to deploy first.

Regarding your second problem, you have to post your conkyrc configuration file for somebody to look at. I don't know if I can help you any further.

---

### Post by wildmanne39 on 2015-05-16
Please use url's or thumbnails when posting images because many people have slow connections and can not load pages with large images.
Thanks

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> esmarra@esmarra-HP-Compaq-6720s:~$ ps -eo pid,cmd | grep conky
 6179 conky -c /home/esmarra/.conky/**[COLOR="#FF0000"]Flat-Wheater[/COLOR]**/conkyrc
 6364 grep --color=auto conky




[http://i.imgur.com/aMShIYL.png](http://i.imgur.com/aMShIYL.png)
You have the path to your conkyrc file wrong.
Conky can't find the file at this path so is loading the default config from **/etc/conky/conky.conf**

The command to start your conky should be ...
```
conky -c ~/.conky/**[COLOR="#FF0000"]Flat-Weather[/COLOR]**/conkyrc
```

If you add conky to startup applications use the inbuilt **-p <secs>** option to pause the starting of conky
until the window manager has loaded.
eg
```
conky **-p 20** -c ~/.conky/Flat-Weather/conkyrc
```

Also, if using Unity, in your "~/.conky/Flat-Weather/conkyrc" config make sure **own_window_type** is normal.
eg 
```
own_window_type **normal**
```

---

### Post by esmarra on 2015-05-17
I put this code in terminal
conky -c ~/.conky/**[COLOR=#FF0000]Flat-Weather[/COLOR]**/conkyrc
[http://i.imgur.com/hR8Jnxa.png](http://i.imgur.com/hR8Jnxa.png)
appear this error!

---

### Post by esmarra on 2015-05-17
conkyrc


```
update_interval 1.0total_run_times 0


alignment tr
gap_x 30
gap_y 75


use_xft yes
override_utf8_locale yes
xftfont Sans:size=9


border_width 0
border_inner_margin 0
border_outer_margin 0
draw_shades no


own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0


max_text_width 0


default_color FFFFFF
color1 FFFFFF


text_buffer_size 384
double_buffer yes
no_buffers yes


imlib_cache_size 0


TEXT
${execpi 60 ~/.conky/Flat-Weather/weather.sh -p "Buenos Aires" -i "ARBA0009" -l "es" -f "Zekton" -S 55 -b -t -w -u -y 3}
```

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> I put this code in terminal
conky -c ~/.conky/**[COLOR=#FF0000]Flat-Weather[/COLOR]**/conkyrc```
http://i.imgur.com/hR8Jnxa.png
```
appear this error!

Copy and paste your terminal output from...
```
ls ~/.conky 
```

Also go to your conkyrc file in your file browser and right click on it and choose "Copy"
Paste that path into the forums.

---

### Post by esmarra on 2015-05-17
[http://i.imgur.com/ZRKbrA8.png](http://i.imgur.com/ZRKbrA8.png)

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> ```
http://i.imgur.com/ZRKbrA8.png
```
That seems ok but your first pic says it can't find weather.sh

Your terminal output from 
```
ls ~/.conky/Flat-Weather/scripts
```

Just copy and paste the output rather than screenshots.

---

### Post by esmarra on 2015-05-17
```
http://i.imgur.com/TBpsk4s.png
```

---

### Post by CantankRus on 2015-05-17
The last line in your conkyrc is calling the wrong path to weather.sh
```
${execpi 60 [COLOR="#B22222"]~/.conky/Flat-Weather/weather.sh[/COLOR] -p "Buenos Aires" -i "ARBA0009" -l "es" -f "Zekton" -S 55 -b -t -w -u -y 3}
```
Should be 
```
[COLOR="#B22222"]~/.conky/Flat-Weather**/scripts**/weather.sh[/COLOR]
```

Also you have set it to update every 60 secs with "execpi 60"
You don't want to check these sites too often.
Some have limits and may ban your IP.
Set to every 5 mins....."execpi 300"

The start conky command should now work...
```
conky -c ~/.conky/Flat-Weather/conkyrc
```

---

### Post by esmarra on 2015-05-17
```
http://i.imgur.com/cHa4rvH.png
```

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> ```
http://i.imgur.com/cHa4rvH.png
```

Same as what I get when using your conkyrc.
Run...
```
killall conky
``` to get rid of the default conky then start conky again.

---

### Post by esmarra on 2015-05-17
When i restart the computer, this appears on the desktop this image. However should appear the image of weather?

[IMG]http://i.imgur.com/UGcGlJW.png[/IMG]

Next 

[COLOR=#000000][I]I put this code in terminal
[/I][/COLOR][COLOR=#000000]*conky -c ~/.conky/*[/COLOR]**[COLOR=#FF0000]Flat-Weather[/COLOR]/conkyrc**[COLOR=#000000][/COLOR]```
http://i.imgur.com/QEee2BJ.png
```

Should appear the image without the black square, right!
One question, when I type this command in Terminal:
[COLOR=#FFFFFF][FONT=Ubuntu Mono]gedit /home/jorge/.conky/Flat-Weather/conkyrc
[/FONT][/COLOR]

appears is blank page conkyrc? It should not appear that the codes?
```
http://i.imgur.com/UDDJCGA.png
```

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> When i restart the computer, this appears on the desktop this image. However should appear the image of weather?



Next 

[COLOR=#000000][I]I put this code in terminal
[/I][/COLOR][COLOR=#000000]*conky -c ~/.conky/*[/COLOR]**[COLOR=#FF0000]Flat-Weather[/COLOR]/conkyrc**[COLOR=#000000][/COLOR]```
http://i.imgur.com/QEee2BJ.png
```

Should appear the image without the black square, right!
One question, when I type this command in Terminal:
[COLOR=#FFFFFF][FONT=Ubuntu Mono]gedit /home/jorge/.conky/Flat-Weather/conkyrc
[/FONT][/COLOR]

appears is blank page conkyrc? It should not appear that the codes?
```
http://i.imgur.com/UDDJCGA.png
```

This
```
gedit /home/**[COLOR="#B22222"]jorge[/COLOR]**/.conky/Flat-Weather/conkyrc
```
From what I have seen, **[COLOR="#B22222"]jorge[/COLOR]** is not your username.

Would it not be...  
```
gedit /home/**[COLOR="#B22222"]esmarra[/COLOR]**/.conky/Flat-Weather/conkyrc
```
or 
you can substitute "~" for "**/home/[COLOR="#696969"]username[/COLOR]**" which will open that file on anyone's computer.
```
gedit ~/.conky/Flat-Weather/conkyrc
```

If you're seeing that image at startup it means you have added the wrong command to startup applications.
```
conky -p 20 -c ~/.conky/Flat-Weather/conkyrc
```

---

### Post by esmarra on 2015-05-17
```
[COLOR=#000000][FONT=Ubuntu Mono]gedit /home/[/FONT][/COLOR]**[COLOR=#B22222]jorge[/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/.conky/Flat-Weather/conkyrc
```
you have right! it my username esmarra its ok.[/FONT][/COLOR]

---

### Post by esmarra on 2015-05-17
its is comand [COLOR=#000000] command to startup applications.[/COLOR][COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG] Attached Thumbnails[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262035&stc=1&thumb=1&d=1431882243[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=262035&d=1431882243")  


[/COLOR]
dont appear nothing when i restart the computer

---

### Post by CantankRus on 2015-05-17
> **esmarra said:**
> its is comand [COLOR=#000000] command to startup applications.


[/COLOR]
dont appear nothing when i restart the computer
Copy and paste the command from startup applications into a terminal and look for errors.
Conky will take 20 secs to appear because of the "-p 20" option.

---

### Post by esmarra on 2015-05-17
conkyrc
```

update_interval 1.0
total_run_times 0


alignment tr
gap_x 1030
gap_y 600


use_xft yes
override_utf8_locale yes
xftfont Sans:size=9


border_width 0
border_inner_margin 0
border_outer_margin 0
draw_shades no


own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0


max_text_width 0


default_color FFFFFF
color1 FFFFFF


text_buffer_size 384
double_buffer yes
no_buffers yes


imlib_cache_size 0


TEXT
${execpi 60 ~/.conky/Flat-Weather/scripts/weather.sh -p "Buenos Aires" -i "ARBA0009" -l "pt" -f "Zekton" -S 55 -b -t -w -u -y 3}
```

Comand startup
```
conky -c /home/esmarra/.conky/Flat-Weather/conkyrc
```

At this moment everything works, just keep the black square

```
http://i.imgur.com/v8wjh9q.png
```

---

### Post by CantankRus on 2015-05-17
You may not be able to use argb transparency with your graphics card/driver.
Comment "[COLOR="#B22222"]#[/COLOR]" the last 2 lines of this section of the conkyrc as shown.
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
[COLOR="#B22222"]#[/COLOR]own_window_argb_visual yes
[COLOR="#B22222"]#[/COLOR]own_window_argb_value 0
```
Save and
```
killall conky
```
and restart conky.

---

### Post by esmarra on 2015-05-17
finally solved the problem:)
The problem was in the code inside the file conkyrc!

Do you know if it is possible to add another conky, like this Cowon Conky!

---

### Post by CantankRus on 2015-05-17
You can run as many configs as you like.
```
conky -c [COLOR="#808080"]/path/to/config[/COLOR]
```

A conky config can be saved anywhere and named anything.
The important thing is paths.
Path to the config and the paths in the conky configs that call scripts or images it may use.

**PS:** You're missing the Zekton font that your Flat-Weather config uses.
[http://www.dafont.com/zekton.font](http://www.dafont.com/zekton.font)
Extract and move the zekton folder to your **/home/esmarra/.fonts** folder.
Create the **.fonts** folder if it doesn't exist.

---

### Post by esmarra on 2015-05-17
I dont folder its this name .fonts?

---

### Post by CantankRus on 2015-05-17
Create it.
Folders and files starting with a dot "." are hidden.
In the file browser press ctrl+h to show hidden.
Hidden files in your home folder are mostly user settings and config files.

---

