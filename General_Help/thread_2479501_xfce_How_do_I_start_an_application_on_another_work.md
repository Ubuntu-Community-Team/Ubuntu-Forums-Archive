---
title: "xfce: How do I start an application on another workspace on autostart?"
date: 2022-09-26
forum: General Help
---

### Post by salamilimos on 2022-09-26
Running Xubuntu 20.04, I'll be upgrading next year.

I want to launch PulseEffects on autostart, but I want it to launch on Workspace 4. Here's my attempts:

```
wmctrl -l -x
0x0440000a  3 pulseeffects.Pulseeffects  salamilimos-PC PulseEffects

flatpak run com.github.wwmm.pulseeffects && wmctrl -x -r 'pulseeffects.Pulseeffects' -t 3

flatpak run com.github.wwmm.pulseeffects && wmctrl -x -r 'pulseeffects' -t 3

flatpak run com.github.wwmm.pulseeffects && wmctrl -x -r 'PulseEffects' -t 3

flatpak run com.github.wwmm.pulseeffects && wmctrl -F 'pulseeffects' -t 3
```

These commands didn't work, PulseEffects loaded on the Workspace I was on instead of on Workspace 4, as I wanted.

Note, I have another instance of [FONT=courier new]wmctrl[/FONT] running though, this is my video wallpaper which I set on autostart, could this be interfering with this?

```
bash -c "sleep 2; mpv -loop-file=inf --no-stop-screensaver --no-audio --osc=no --cursor-autohide=no --no-input-default-bindings --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') '/home/salamilimos/Videos/.Razer loop RGB Full HD 60fps Chroma background for   Wallpaper Engine [5le-dkHZLd0].mp4'"
```

---

### Post by &amp;KyT$0P# on 2022-09-26
Those commands don't run [FONT=Courier New]wmctrl[/FONT] until after PulseEffects quits, and will only run it if PulseEffects exits with status 0 (success).

Step 1 is to figure out a [FONT=Courier New]wmctrl[/FONT] command that you can run manually, while PulseEffects is running, to move it to Workspace 4.

Once you have that, then you could write a bash script to run PulseEffects in the background (just one [FONT=Courier New]&[/FONT] not two), then loop checking [FONT=Courier New]wmctrl[/FONT] output for the presence of the PulseEffects window and if it's there, run the [FONT=Courier New]wmctrl[/FONT] command you found to move PulseEffects to Workspace 4 and then exit the script.

---

### Post by guiverc on 2022-09-26
You realize Xfce can restore set applications at session start.

Refer [https://docs.xfce.org/xfce/xfce4-session/start](https://docs.xfce.org/xfce/xfce4-session/start)

> *Xfce4-session* is a session manager for Xfce. Its task is to  save the state of your desktop (opened applications and their location)  and restore it during a next startup. You can create several different  sessions and choose one of them on startup.

---

### Post by salamilimos on 2022-09-27
> **halogen2 said:**
> Those commands don't run wmctrl until after PulseEffects quits, and will only run it if PulseEffects exits with status 0 (success).

Step 1 is to figure out a wmctrl command that you can run manually, while PulseEffects is running, to move it to Workspace 4.

Once you have that, then you could write a bash script to run PulseEffects in the background (just one & not two), then loop checking wmctrl output for the presence of the PulseEffects window and if it's there, run the wmctrl command you found to move PulseEffects to Workspace 4 and then exit the script.

Running these commands in two terminals works though:

Opens PulseEffects:
```
flatpak run com.github.wwmm.pulseeffects
```

Moves PulseEffects to Workplace 4:
```
wmctrl -r PulseEffects -t 3
```

However, putting these together in a command doesn't work though:

```
flatpak run com.github.wwmm.pulseeffects && sleep 25 && wmctrl -r PulseEffects -t 3
```

I figured out a dirty workaround:

I created two .desktop files and saved them in /home/salamilimos/.config/autostart/ with the following:

```
[Desktop Entry]
Version=1.1
Type=Application
Exec=bash -c "sleep 5 && flatpak run com.github.wwmm.pulseeffects"
```

and

```
[Desktop Entry]
Version=1.1
Type=Application
Exec=bash -c "sleep 20 && wmctrl -r PulseEffects -t 3"
```

They worked.

I no idea why putting the two commands together doesn't work though.

---

### Post by salamilimos on 2022-09-27
> **guiverc said:**
> You realize Xfce can restore set applications at session start.

Refer [https://docs.xfce.org/xfce/xfce4-session/start](https://docs.xfce.org/xfce/xfce4-session/start)

I couldn't figure this out though.

---

### Post by &amp;KyT$0P# on 2022-09-27
> **salamilimos said:**
> putting these together in a command doesn't work though:

```
flatpak run com.github.wwmm.pulseeffects && sleep 25 && wmctrl -r PulseEffects -t 3
```

Again, because the way you are putting them together means PulseEffects must exit with a success status before the [FONT=Courier New]sleep[/FONT] and [FONT=Courier New]wmctrl[/FONT] commands are run.  To achieve what you want, use **only one [FONT=Courier New]&[/FONT]** after the PulseEffects command.

> I figured out a dirty workaround:

I created two .desktop files and saved them in /home/salamilimos/.config/autostart/ with the following:

That's pretty close to one possible actual solution.

You could combine your two desktop files into one -
```
[Desktop Entry]
Version=1.1
Type=Application
Exec=bash -c "sleep 5;flatpak run com.github.wwmm.pulseeffects & sleep 20;wmctrl -r PulseEffects -t 3"
```

---

### Post by salamilimos on 2022-09-27
> **halogen2 said:**
> You could combine your two desktop files into one -

```
[Desktop Entry]
Version=1.1
Type=Application
Exec=bash -c "sleep 5;flatpak run com.github.wwmm.pulseeffects & sleep 20;wmctrl -r PulseEffects -t 3"
```

That worked thank you.

So, my previous attempts failed because I was using two "&&" instead of one "&"? Based off my reading of your posts, the difference between "&" and "&&" is that using one "&" doesn't allow the program to exit while the next command runs, while "&&" exits the program and does the next command. Is this correct? I'm not exactly terminal savvy.

---

### Post by &amp;KyT$0P# on 2022-09-27
You're welcome. :KS

> **salamilimos said:**
> So, my previous attempts failed because I was using two "&&" instead of one "&"? 

Yes, that was dooming your previous attempts to fail.

> Based off my reading of your posts, the difference between "&" and "&&" is that using one "&" doesn't allow the program to exit while the next command runs, while "&&" exits the program and does the next command. Is this correct? 

Using just one & after a command means "run the command in the background", i.e. free up the shell to continue on with running other commands without waiting for that command to exit.

"&&" is something completely different.  It is used to chain two commands together.  The command on its right will not run unless and until the command on its left exits with the success status 0.

Hope this helps clarify.

---

### Post by salamilimos on 2022-09-27
> **halogen2 said:**
> You're welcome. :KS



Yes, that was dooming your previous attempts to fail.



Using just one & after a command means "run the command in the background", i.e. free up the shell to continue on with running other commands without waiting for that command to exit.

"&&" is something completely different.  It is used to chain two commands together.  The command on its right will not run unless and until the command on its left exits with the success status 0.

Hope this helps clarify.

Thanks for the explanation. I learn something new everyday. Thanks!

---

