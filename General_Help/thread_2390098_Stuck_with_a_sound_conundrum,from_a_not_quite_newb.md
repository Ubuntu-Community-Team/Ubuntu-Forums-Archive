---
title: "Stuck with a sound conundrum,from a not quite newbie"
date: 2018-04-25
forum: General Help
---

### Post by gr8fun on 2018-04-25
Hi All.
I've been playing around with Linux and Ubuntu on and off for some time. This time was a result of how Windows 10 think they can just reboot your PC when they want!!  I'm still a little angry but I'm loving Ubuntu 17.10!

To my great satisfaction I have managed to get everything I used to use in windoze working fine in my Ubuntu 17.10 desktop....  Except one thing...

The scenario is I have a windows security server that monitors 4 cameras for motion and saves the videos appropriately.  One camera monitors the front of the house and on detecting movement it will run a python script on the windows security server.
This script simply calls an index.php on my Ubuntu desktop - it does nothing more than plays a sound file and (hopefully) brings a Firefox browser window to the fore.
I've install Lampp and it all looks great, web pages being served etc.

The index.php file contains
[PHP]<?phpshell_exec('python /opt/lampp/htdocs/test/bell.py'); 
echo "done";
?>[/PHP]

This** bell.py** came off the win10 box I have now setup as Ubuntu and had a few tweaks to get the python working in a terminal
```
#!/usr/bin/env python#coding=utf-8  


import pyaudio  
import wave  


#define stream chunk   
chunk = 1024  


#open a wav format music  
f = wave.open(r"/opt/lampp/htdocs/test/bell.wav","rb")  
#instantiate PyAudio  
p = pyaudio.PyAudio()  
#open stream  
stream = p.open(format = p.get_format_from_width(f.getsampwidth()),  
                channels = f.getnchannels(),  
                rate = f.getframerate(),  
                output = True)  
#read data  
data = f.readframes(chunk)  


#play stream  
while data:  
    stream.write(data)  
    data = f.readframes(chunk)  


#stop stream  
stream.stop_stream()  
stream.close()  


#close PyAudio  
p.terminate()  



```

This code plays the sound file fine from my home directory running "python /opt/lampp/htdocs/test/bell.py"
or with just  "./bell.py" from the /opt/lampp/htdocs/test directory.
So I'm guessing the code is OK

The directory test has settings of[B] drwxrwxr-x 2 dan www-data 
[/B]and the files have the same security

The **daemon**  user has been added to the **www-data** group as has **dan. **I believe it is the daemon usaer that runs the script when done form the webpage
 
When I access the php page I see no errors, but have no sound played.

Any ideas on next steps

---

