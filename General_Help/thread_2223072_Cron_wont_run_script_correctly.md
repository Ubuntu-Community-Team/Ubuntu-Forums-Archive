---
title: "Cron wont run script correctly"
date: 2014-05-09
forum: General Help
---

### Post by PlugInPrius on 2014-05-09
I have a script that I put together from doing some searching and here is what I got. I'm trying to grab an image from an IP camera and upload it to my website. If the camera is offline I want to upload an offline image in place of the camera image. Here is what I tried.


```
wget http://192.168.0.136:8080/shot.jpg
if [ $? -ne 0 ]
 then sshpass -p 'MyPassword' scp offline.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg

  else mv shot.jpg traffic.jpg && sshpass -p 'MyPassword' scp traffic.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg
fi
```

I've also tried this

```

wget http://192.168.0.136:8080/shot.jpg && mv shot.jpg traffic.jpg && sshpass -p 'MyPassword' scp traffic.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg || sshpass -p 'MyPassword' scp offline.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg
```

Both run perfectly from the command line but when cron runs the script it will not upload the offline image if the camera is offline. It will upload the image just fine when the camera is working.

I've even tried using echo to put some text in a log file so I could see that it executed the command but cron wont even do that.

Why wont cron run the offline part of the script correctly?

---

### Post by Toz on 2014-05-09
The cron environment variables (including $PATH and the current working directory) are different than your user environment variables. I would try specifying the full complete path name to the offline.jpg file. Its quite possible that cron can't find it.

---

### Post by PlugInPrius on 2014-05-09
It cant find it but its in the same directory as the shot.jpg and traffic.jpg? I'll give it a try and report back.

---

### Post by Vaphell on 2014-05-09
afaik full paths are a must in cron

wrap the contents of your script with {} and redirect it to some file with predictable location, eg

```
{
    wget=/usr/bin/wget
    sshpass=/usr/bin/sshpass
    scp=/usr/bin/scp
    mv=/bin/mv
    pw='MyPassword'

    "$wget" http://192.168.0.136:8080/shot.jpg
    if [ $? -ne 0 ]
    then
        "$sshpass" -p 'MyPassword' "$scp" offline.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg
    else
        "$mv" shot.jpg traffic.jpg && "$sshpass" -p "$pw" "$scp" traffic.jpg MyUsername@MyDomain.com:MyDomain.com/traffic.jpg
    fi
} > /some/dir/debug.txt 2>&1
```

you will have something to debug.

---

### Post by PlugInPrius on 2014-05-09
Thanks Vaphell. Your script worked. I just had to fix the $"scp" I think you mistyped and add a full path for the offline.jpg. Thanks again.

---

### Post by PlugInPrius on 2014-05-16
I found a small issue with this script or more like wget. I made the following changes just in case anyone else might want to use this.

"$wget" -T 10 --tries=1 [http://192.168.0.136:8080/shot.jpg](http://192.168.0.136:8080/shot.jpg)

When my camera stopped responding wget would just hang and stop the script from continuing. So I told wget to timeout quickly if it does not get a response.

Now the script works much better.

---

### Post by PlugInPrius on 2014-06-12
Here is an updated script. This will only upload the offline picture once to save bandwidth.

```
{
    wget=/usr/bin/wget
    sshpass=/usr/bin/sshpass
    scp=/usr/bin/scp
    touch=/usr/bin/touch
    mv=/bin/mv
    rm=/bin/rm
    pw='MyPassword'

    "$wget" -T 10 --tries=1 http://192.168.0.136:8080/shot.jpg
    if [ $? -ne 0 ]
    then
        if [ -f /media/Media/Scripts/tmp ]
        then
           echo "File exists"
        else
           echo "File does not exists" && "$touch" /media/Media/Scripts/tmp && echo "Created tmp file" && "$sshpass" -p "$pw" "$scp" /media/Media/Scripts/offline.jpg  MyUserName@Mydomain.com:Mydomain.com/traffic.jpg && echo "Finished uploading"
        fi
     else
        if [ -f /media/Media/Scripts/tmp ]
        then
           echo "File exists" && "$rm" /media/Media/Scripts/tmp && echo "Removed tmp file" && "$mv" shot.jpg traffic.jpg && "$sshpass" -p "$pw" "$scp" traffic.jpg MyUserName@Mydomain.com:Mydomain.com/traffic.jpg && echo "finished uploading"
        else
           "$mv" shot.jpg traffic.jpg && "$sshpass" -p "$pw" "$scp" traffic.jpg  MyUserName@Mydomain.com:Mydomain.com/traffic.jpg && echo "finished uploading"
        fi
    fi
}
```

So far it works perfectly. If anyone sees any issues with this script let me know. I know how to program but not very well and or not very optimized. :)

---

