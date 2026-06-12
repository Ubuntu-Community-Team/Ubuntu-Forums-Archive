---
title: "Speed issues"
date: 2006-11-28
forum: General Help
---

### Post by kaylus on 2006-11-28
**NOTE: THIS IS NOT POSTED FOR DEBATE OR SUBJECTIVE ANALYSIS/OP-EDS. I AM LOOKING FOR HELP NOT DEBATE.**

I currently use Ubuntu. It is the first time i've used the Gnome desktop for more than a few days and I absolutely adore it. Be that as it may, I still decided to give Kubuntu a go. I used the same computer and the exact same partition scheme. I then installed the default Kubuntu off of the Live-CD and used Automatix to add the same things I added under my Ubuntu Distro (Skype, Firefox add-ons, Codecs, etc).

I had a nicely running system, except for one thing, things run much slower than they did on Gnome. At first I assumed that this was merely in my head, the bouncing icon and animation of things booting up contributing to the impatience I already had. Unfortunately, I was wrong.

I switched between the systems numerous times (via reinstall) and always the Kubuntu/KDE was slower. In points getting so slow that my keypresses lagged, while gnome with the same amount of applications and then-some did not display the same slowdown.

One showdown was using Cedega to play Morrowind. It worked well on both, but under KDE with Morrowind open under CEDEGA, Konsole open, Kate open, Kopete Open, I clicked on Firefox and after 30 seconds the loading icon on the taskbar dissapeared, and another attempt at starting it up gave me an error after 25 seconds that Firefox was already trying to open or some such nonsense. Under Gnome/UBUNTU I didn't have similar issues.

Now, this may sound like a rant, but it is not... why do I need help? Because i'd like to get an operational version of Kubuntu up, so I can evaluate it fairly. I want to know why KDE is running so slow on my setup. Is there anything I can check to find out why this is running so slow? Are there settings I can change? 

System:
AMD Athlon 2800+, 768mb Memory
/ - 120gb WD 7200 RPM
/hdb1 - 250gb WD 7200 RPM
/hdd1 - 80gb WD 7200 RPM
Nvidia Ti4200 AGP w/128mb DDR

---

### Post by reclusivemonkey on 2006-11-28
> **kaylus said:**
>  Are there settings I can change? 


Yes. There is a wizard in KDE to alter the amount of "eye-candy" KDE uses. Its a *long* time since I used KDE, on Slackware this automatically run when you first logged in to KDE (which is the only place I've used KDE). You should be able to find it somewhere in that vast KDE menu ;-)

---

### Post by kaylus on 2006-11-28
I just can't imagine "eye-candy" being the cause of so much slowdown. As I mentioned already, I can manage playing Elder Scrolls Morrowind in a Window while doing numerous other things without slowdown in gnome, and that's not a graphics-lite baby. 

Would the eye-candy really amount to that much? I've used Compiz/Beryl etc overlaid w/Gnome and didn't get the same thing --- so I hope it isn't! A little more information

768MB PC2700 RAM
GeForce Ti4200 w/ 128mb Ram (yes, it's a bit older :D)

When running under KDE I felt like I was using Windows XP on a 300mhz machine w/128mb-ram instead of KDE on a AMD2800+ w/768mb-ram... I have been looking over the internet and i've seen various reports of people claiming one or the other is slower and it's all computer dependent and all -- blah blah... I can't truly believe that! There has to be something somewhere that makes it slower on one computer over another...

Regards

---

### Post by kaylus on 2006-12-02
After running a bit of transcoding, i'm not so sure it is the Desktop itself after all. I am using transcode on a video file at 34fps transcoding speed, which is fine. When I was in KUBUNTU the speed was invariably always 18fps, and sometimes lower. Could there actually be something wrong with how Kubuntu is interacting with my system?

---

### Post by reclusivemonkey on 2006-12-03
> **kaylus said:**
> I just can't imagine "eye-candy" being the cause of so much slowdown. As I mentioned already, I can manage playing Elder Scrolls Morrowind in a Window while doing numerous other things without slowdown in gnome, and that's not a graphics-lite baby.

No offence, but it doesn't matter what you think ;) . Its worth trying to see if it makes a difference and its easy to do. We are trying to troubleshoot here, so you try what you can and see the results. If you turn down all the "eye candy" in KDE and it runs faster, you are onto something. If it doesn't make a difference you know you need to keep on looking.

> **kaylus said:**
> Would the eye-candy really amount to that much? I've used Compiz/Beryl etc overlaid w/Gnome and didn't get the same thing --- so I hope it isn't! A little more information

Totally different. Compiz/Beryl uses your graphics card to display eye candy. That's actually taking pressure *OFF* your CPU and RAM. That's the whole reason behind Beryl/Compiz; to use your PC's resources more effectively. The eye candy is just an added extra.

Its impossible for me to tell you what the problem is, only for me to offer things to try. If you don't want to try them, then I can't offer much more advice.

If speed and response are the main concerns for your desktop, you should run a more lightweight desktop, like XFCE or Fluxbox.

---

### Post by kaylus on 2006-12-04
I turned off the eye candy, and as expected it made not a single difference. I know you are assisting in trouble-shooting, and I thank you for it. I'm attempting to try to trouble-shoot it myself as well.

You say " If speed and response are the main concerns for your desktop, you should run a more lightweight desktop, like XFCE or Fluxbox."

While I understand that these are lovely responses, this does not help. No offence intended, but: Painting an egg red does not make it a ruby.

A modern operating system w/GUI should be able to run extremely well on the specifications given. KDE runs faster on both my laptop w/half the power and my SuSE server on a system with a 1.5ghz and 256mb less ram.

This isn't about "speed and response", it's about finding out why this KDE on this distro is many multiple times slower than both the Gnome distro (which are supposed to be identical except desktop and some packages) and every other KDE distro i've tried (not alot: SuSE, Mandr, RedHat), and how I might go about fixing it, or get a better and more indepth look at the why of things.

If it runs so horribly for no apparent reason on this system and the only answer given is "Turn off eyecandy or switch to a different desktop", then don't you think that may have the effect of turning people off this distro? Isn't that antithetical to the primary goal?

I thank you for the time you've taken to respond to me, have a nice night.

---

### Post by jhuff on 2006-12-05
I agree with you.  I am a long time Ubuntu user and have used Gnome.  I installed the kubuntu 6.10 and it is very slow.  Just switching between desktops using the preview function in the task bar was very slow. I installed PCLinuxOS and I have no speed issues.  This seems to be a problem with Kubuntu.  Does anyone have any ideas?

---

### Post by Watter on 2006-12-12
I have had the same problem with Edgy, and to a smaller degree Dapper. Kubuntu is running chunk-ily. When I switch over to Ubuntu, everything is back to snappy. I have OpenSuse(w/KDE), Ubuntu, and Kubuntu all installed on the same machine and while OpenSuse and Ubuntu are speedy, Kubuntu is running slow. It's not a huge massive "something is obviously wrong here!" kind of slow, it's just not very snappy. Dragging windows causes hiccups. Alt-tabbing between windows taks too long because of the redraw. Each individual item isn't too bad, but they all add up together to be a fairly annoying user experience, and this is coming from a dedicated Kubuntu user. I stronly prefer it over Ubuntu/Gnome. 

The machine in question: Pentium D 940, 2Gb ram, Nvidia GeForce 6200TC

I'd love to figure out how to get Kubuntu back to its old nimble self.

---

