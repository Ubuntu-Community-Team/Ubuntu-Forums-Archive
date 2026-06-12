---
title: "Help With a Zenity Script"
date: 2014-02-23
forum: General Help
---

### Post by garyzw on 2014-02-23
I'm trying to write a simple script for youtube-dl with Zenity-- I'm new to this and trying to learn--thanks for any help.

This is my code

```
#!/bin/bash
down_path=/home/$USER/Desktop
you_url=`zenity --entry --text "Paste URL Youtube" --title "Youtube Downloader"`
file=`youtube-dl --get-filename $you_url`
cd $down_path
if [ "$?" = "0" ]; then (youtube-dl $you_url) | zenity --progress --width=300 --height=100 --title="Download" --text "Video download in progress..." --pulsate auto-close 
if [ "$?" = "1" ]; then zenity --title="Youtube Downloader" --info --text="Video Download Cancelled." --auto-kill
zenity --info --window-icon="info" --text="Video Download to Desktop Complete"
exit 1

```

---

### Post by Habitual on 2014-02-24
quote your variables 
cd "$down_path"

what's the issue presently?

---

### Post by tgalati4 on 2014-02-24
Exit status would normally be 0 at the end of a successful script.  You could include "exit 1" after your cancel line ("$?"="1") or use an else-if construction.

Put some documentation at the beginning of the script. Also, it would be a good idea to include a zenity notice about YouTube's [terms of service]("http://www.youtube.com/static?gl=us&template=terms").

---

### Post by garyzw on 2014-02-24
> **tgalati4 said:**
>   You could include "exit 1" after your cancel line ("$?"="1") or use an else-if construction.


That was the reason I could not cancel 
Thanks

---

