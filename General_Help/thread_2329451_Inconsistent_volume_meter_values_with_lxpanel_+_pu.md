---
title: "Inconsistent volume meter values with lxpanel + pulseaudio"
date: 2016-07-01
forum: General Help
---

### Post by leozinho29_eu on 2016-07-01
Hello

I have installed pulseaudio in my computer due to alsa issues with Audacious + Kerbal Space Program + Steam + Skype. One of them would always be mute and Unity3D games were not working due to some strange bug (their bug). Pulseaudio works very well after being installed in Lubuntu 16.04 (with 14.04, pulseaudio was horrible). However, one issue always happen:

The volume controller in Lubuntu is not consistent.

Mouse wheel: when set zero, it makes all the volumes zero and any change to above raises all them to 100 unless Master. This is what the other desktop interfaces do.

Keyboard's multimedia buttons: only the master volume is changed, even at zero. This results in inconsistent indications of the volume meter.

Examples of the results using the keyboard: 
-No sound in lxpanel is 9 (nine) and not 0 (zero)
-Maximum sound in lxpanel is 99 (ninety nine) and not 100 (one hundred)

And that numbers are not consistent: sometimes that nine will be eleven and the ninety nine will be ninety four.

The main issue is, however, one that is very annoying especially due to full screen applications. If I reduce the volume to zero using the mouse wheel, I can't raise it using the keyboard. This happens because the mouse wheel reduces to zero all the volumes and the keyboard don't change them, so nothing triggers the other volumes to raise, which results in no sound using the keyboard multimedia buttons. To recover it, I just need to use the mouse wheel again. 

I would like to know exactly which package(s) is/are the affected one(s) and if there is a configuration that, if I change, can make the keyboard multimedia buttons control volume as the other interfaces and the mouse wheel do, which would make lxpanel mark the values consistently. 

Thank you

---

### Post by leozinho29_eu on 2016-07-02
After searching more and doing more tests about this, looks like the lxpanel is not the responsible for the issue, the issue is with the keyboard multimedia buttons doing volume adjustments differently from mouse wheel.

How could I configure the multimedia buttons to control the volume as the mouse wheel and the other desktop interfaces do?

---

### Post by leozinho29_eu on 2016-07-06
After reading [this question,]("http://superuser.com/questions/209944/use-volume-keys-under-linux") I have found the file with the problematic configuration.

The problem was in the Openbox configuration file at ~/.config/openbox/lubuntu-rc.xml. The volume was being changed using alsa and not pulseaudio. As the old default was alsa only, it was not a surprise. To solve, I had to change the following lines from:

```
   <keybind key="XF86AudioRaiseVolume">
        <action name="Execute">
            <command>amixer -q sset Master 3%+ unmute</command>
        </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
        <action name="Execute">
            <command>amixer -q sset Master 3%- unmute</command>
        </action>
    </keybind>
    <keybind key="XF86AudioMute">
        <action name="Execute">
            <command>amixer -q sset Master toggle</command>
        </action>
    </keybind>
```

To:

```
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ +2%</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ -2%</command>
      </action>
    </keybind>
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>pactl set-sink-mute @DEFAULT_SINK@ toggle</command>
      </action>
    </keybind>
```

This way, I can raise the volume using the multimedia keys even after reducing the volume to zero using mouse wheel or the volume icon at lxpanel.

However, now I can raise the volume using keyboard to values way above 100% (I had patience to reach 814%). I would like to limit the volume that can be reached using the keyboard to 63% (it is labelled as "Básico" in pavucontrol) or another value. I bet it would be hard to find new speakers for my notebook. I can't raise the volume to above 100% using the mouse and I can reduce it from any value above 100% to 100% instantly with it.

Now I have to search a way to limit how much I can raise the volume using the keyboard. It would be something like a "if" that checks if the volume is above a certain value (63% as example) and then it do not allow to increase the volume further. I tried my best to create a script which checks the actual volume to see if it would be allowed to be increased. I have found a way [here]("http://unix.stackexchange.com/questions/132230/read-out-pulseaudio-volume-from-commandline-i-want-pactl-get-sink-volume") to see the actual pulseaudio volume. 

Adding another command to the originally proposed, I made this command: 

```
amixer -c 0 -M -D pulse get Master | grep -o -E [[:digit:]]+% | grep -o -E +[[:digit:]]+
```

Which outputs: 

```
44
44
```

I would like to get the highest actual value (if they are different) and compare it with the maximum I set in the script (63). If the actual value is lower than the limit I set (63) then it will allow the volume increase, else it will do nothing. I was unable even to create a variable with that values, I don't know how to program above a certain threshold. Then I would set that script in the openbox configuration when the raise volume button is pressed.

---

### Post by leozinho29_eu on 2016-07-12
I was able to solve the issue.

I have found a script that does exactly what I was trying to do: it checks the actual volume, set a threshold and limits the volume.

I found it here: [https://bbs.archlinux.org/viewtopic.php?id=124513](https://bbs.archlinux.org/viewtopic.php?id=124513)

With it, I can limit the volume that can be reached using keyboard. I had to change the Openbox configuration file again.

 The only issue is that the pulseaudio-ctl demands high CPU in its usage. My desktop showed pretty small problems with this, but the notebook suffers a bit. The lower volume and mute/unmute I let pactl to control because this way the CPU usage is lower.

Edit: I have found an option which do not require an additional program. I found it here: [http://askubuntu.com/questions/32383/adjust-pcm-volume](http://askubuntu.com/questions/32383/adjust-pcm-volume) 

As I have stated, the volume had a maximum of 63 and a minimum of 11. Doing the change proposed in the answer, the PCM volume was ignored, so the "Básico" label disappeared. The standard PCM volume was 56, and with this change pulseaudio volume will never change the PCM volume, but it is possible to change using alsamixer. 

However, another volume was being changed and making the indicator shows wrong values: Headphone. To correct this, I had to edit the file analog-output-headphones.conf in the same folder. The edition was the same: substitute merge to ignore, but this time in the options [Element Headphone] and [Element Headphone+LO]. Then the only volume that is relevant is Master. 

With that changes done, I have reconfigured the openbox raise volume again. The Openbox's configuration which is working in lubuntu-rc.xml is: 

```
    <!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q sset Master 2%+ unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ -2%</command>
      </action>
    </keybind>
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>pactl set-sink-mute @DEFAULT_SINK@ toggle</command>
      </action>
    </keybind>
```

I decided to use amixer because this way it is impossible to reach volumes above 100 only with the volume buttons, which pactl allows. To reduce and mute I decided to use pactl because it is the volume controller which consumes less resources and...

...there are bugs too, one that makes pulseaudio indicates that there is still volume even if Master is 0. And the mute option that can't unmute pulseaudio because of the same problematic merge options at that files ( [https://bugs.launchpad.net/xfce4-volumed/+bug/883485](https://bugs.launchpad.net/xfce4-volumed/+bug/883485) ).

Pulseaudio became much better when installed in Lubuntu 16.04 than in Lubuntu 14.04. There are many configuration possibilities which can make everyone find a perfect configuration for its situation, but it was hard to find documentation and help about them. The man pages are good, but finding the terms to open the right ones was hard. The files at /usr/share/pulseaudio/alsa-mixer/paths are important and I believe it lacks documentation to know about them. Once found, the comments at the own files are really helpful. There are 9 favourite pages only due to this issue.

Finally the volume configuration is done. The configuration in /usr/share/pulseaudio/alsa-mixer/paths is different in different computers, so if is needed to make that configurations too, it may be slightly different, but the idea is to make pulseaudio ignore certain volumes.

Now that the volume issue is solved, it is time to find a solution to the IrDA and graphic issues.

---

