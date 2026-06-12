---
title: "No sound after upgrade to 15.04"
date: 2015-05-25
forum: General Help
---

### Post by hans12345 on 2015-05-25
I have no sound.

I have just upgraded (clean installation, maybe a mistake) from 14.04 LTS to 15.04. Only Home data was kept. This is my wife's laptop, and she would never be adventurous and try anything out of the ordinary.

The sound was working well, now after the installation, not a peep.

When I try ideas gleaned from these forums, I often get:

 Fatal Error : Unable to connect to PulseAudio: OK

e.g. if I try to run the PulseAudio Volume Control, I get the message.

I have reinstalled PulseAudio (I always use Synaptics for package management, I feel it is safer. Is it equivalent to 'apt-get remove --purge' and then install? I assume so) with no change.

I have reinstalled Alsa with Synaptics, again no change.

When I started this investigation, the sound display on the top screen bar showed sound was normal. Now it shows that my sound is muted. I have tried but I cannot un-mute.

2 potential complications:
- this laptop runs Xubuntu not Ubuntu, but I assume the sound system should be the same
- I loaded the microcode firmware for Intel CPUs (not open source)

The problem should be simple. This is a nearly clean installation.

Where do I go from here? What extra info can I supply?

Thanks for your help.

---

### Post by mattharris4 on 2015-05-25
Check alsamixer.  Here is a link to instructions to fix several different issues regarding sound but you need section two:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) .

Here is the pertinent info:

PulseAudio controls underlying ALSA-level volume controls. To change the ALSA-level volume controls directly, you can do [[COLOR=#009900]_the following_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#"):Open a terminal. (The quickest way is the **Ctrl-Alt-T** shortcut)Enter** &#8220;alsamixer&#8221;** and press the Enter key.
In this user interface, you can do the following:
[LIST=1]
[*]Select your correct sound card using **F6 and select F5** to see recording controls as well
[*]Move around with left and right arrow keys.
[*]Increase and decrease volume with up and down arrow keys.
[*]Mute/Unmute with the **&#8220;M&#8221;** key. An &#8220;MM&#8221; means muted, and &#8220;OO&#8221; means unmuted.
[*]Exit from alsamixer with the Esc key.
[/LIST]

You will need to follow steps 2-4 with Master, Headphon and Speaker.  If they aren't muted ("MM" under the graph bars means that function is muted) before attempting to change them, you have another issue entirely.

---

### Post by hans12345 on 2015-05-26
> **mattharris4 said:**
> Check alsamixer.  Here is a link to instructions to fix several different issues regarding sound but you need section two:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) .

Here is the pertinent info:

PulseAudio controls underlying ALSA-level volume controls. To change the ALSA-level volume controls directly, you can do [[COLOR=#009900]_the following_[/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#"):Open a terminal. (The quickest way is the **Ctrl-Alt-T** shortcut)Enter** “alsamixer”** and press the Enter key.
In this user interface, you can do the following:
[LIST=1]
[*]Select your correct sound card using **F6 and select F5** to see recording controls as well
[*]Move around with left and right arrow keys.
[*]Increase and decrease volume with up and down arrow keys.
[*]Mute/Unmute with the **“M”** key. An “MM” means muted, and “OO” means unmuted.
[*]Exit from alsamixer with the Esc key.
[/LIST]

You will need to follow steps 2-4 with Master, Headphon and Speaker.  If they aren't muted ("MM" under the graph bars means that function is muted) before attempting to change them, you have another issue entirely.

Thanks Matt.

Master and Headphone were muted. No 'speaker', but a PCM instead?

Master was set to 100%, headphone to 0. 

Now both at 100% and un-muted.

And it WORKS! Thanks again.

What I fail to understand is:
- why should a simple clean installation of 15.04 mute the sound?
- I still get the error message saying no PulseAudio.

But I'm happy.

---

### Post by mattharris4 on 2015-05-26
^  You are welcome, Hans.  Unfortunately I don't know why Lubuntu does that but it is a known problem.  Maybe you could e-mail one of the programmers at Canonical and ask them about this issue.

---

### Post by mörgæs on 2015-05-27
Canonical does not build Xubuntu, it's maintained by the community. 
Even if they did, e-mailing is not the correct way of contacting the developers. Using Launchpad is.

Hans, please mark the thread 'solved'.

---

### Post by mattharris4 on 2015-05-27
^  Thank you for the correction, Morgaes.  I knew Kubuntu was fully community-maintained but was under the impression that Xubuntu, Lubuntu, Edubuntu and the various Ubuntus other than Ubuntu MATE were at least partially maintained by Canonical (as I have said on other threads and you are probably more aware than I according to Canonical some coding and a lot of testing is done by volunteers not employed by Canonical so technically your comment regarding "maintained by the community" is partially appropriate for all Canonical OSes but I thought the appropriate point of contact for the OP's question was there).  I do know that Lubuntu was originally coded outside of Canonical but was under the impression that Canonical took it over when they officially recognized the OS in about 2011.  Since your screen name has "staff emeritus" (which would mean evidently you worked for Canonical directly at one time) you might be in the position to clarify the appropriate contacts for each OS recognized by Canonical.

Also, we have had at least five threads where the "alsamixer" fix was called for in the past two weeks.  Maybe we should have a sticky about it.  If you could please direct me to the instructions for this I would be willing to write it.

---

### Post by mörgæs on 2015-05-28
I don't know how this is 'evidently'.
I have volunteered my time in Ubuntuforums but never worked for Canonical if you mean work as in 'receiving payments' and I am not aware of any forum user who works or worked for them.

---

### Post by spjm69 on 2015-06-21
thank you so much....... never had to deal with this issue before.
fixed it without a hitch
1st time for everything

---

### Post by Keermalec on 2015-08-30
> **hans12345 said:**
> Thanks Matt.

Master and Headphone were muted. No 'speaker', but a PCM instead?

Master was set to 100%, headphone to 0. 

Now both at 100% and un-muted.

And it WORKS! Thanks again.

What I fail to understand is:
- why should a simple clean installation of 15.04 mute the sound?
- I still get the error message saying no PulseAudio.

But I'm happy.

Had the same problem and the above solution worked for me too, but it is not permanent. ie.- every time you log on you have to launch alsamixer and turn on the headphone volume manually.

Here is the permanent solution, using amixer, a command-line tool similar to Alsamixer:

1. create a text file:
sudo gedit

2. copy-paste these two lines into it:
/usr/bin/amixer -c 0 cset iface=MIXER,name='Headphone Playback Volume' 100%
/usr/bin/amixer -c 0 cset iface=MIXER,name='Headphone Playback Switch' 1+ toggle

3. save it as /usr/bin/amixer_script.sh

4. make it executable with sudo chmod +x /usr/bin/amixer_script.sh

5. open System->Control Center->Startup Applications

6. add your script as a start-up application

Now every time you boot up you will have sound.

If it doesn't work, play around with instruction n° 2:
-c 1 instead of -c 0 for the second sound card
man amixer to see all options

Cheers

---

### Post by TapaniS on 2015-09-18
Same problem here. Finally solved somewhat like this:

1. sudo apt-get install paman

2. Followed instructions by [**[COLOR=#000000]Keermalec , [/COLOR]**]("http://ubuntuforums.org/member.php?u=914806")but wrote lines:
        /usr/bin/amixer -c 0 sset Headphone playback 100%
       /usr/bin/amixer -c 0 sset Headphone unmute

3. Needed to set startrup -line as follows: xterm -e /usr/bin/amixer_script.sh 

Thank you, very much! It was much harder than I could imagine, but now it works!

[ASUS Eee PC 1011px + lubuntu 15.04, 64bit]

---

