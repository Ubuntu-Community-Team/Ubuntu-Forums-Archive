---
title: "trying make a custom live-cd bitcoin wallet, without installing linux"
date: 2013-02-25
forum: General Help
---

### Post by merockstar on 2013-02-25
Hey Ubuntu it's been a long time. I've been without a computer of my own for too long now.

And that would be why I'm using other people's computers, this one running Windows 7 at the moment.

Anyway, I've been eyeballing the bitcoin economy for quite some time now, and I think I'm going to start picking up a couple here and there in case they explode.

To that end I was attempting to set myself up with a nice peachy little live-cd environment, which would be running a custom ubuntu with nothing but armory, firefox, tor, and gnupg (and I feel like I'm forgetting something but oh well you get the point). And it could be my secure little money/anonymous browsing computer-vagrant's friend cd.

I don't want to use USB because I don't trust that technology to last me very long, especially running an OS off of it. I feel like a cd would be better for this purpose longevity wise, although I base that on nothing but personal experience. I have come up with a great way to keep the seed to my private key memorized, and it's not something that's going to get cracked. So I am secure in only having one physical copy of my wallet at a time to keep dibs on.

Anyway, what with the nature of cd-r's and stuff, installing everything every time I wanted to use my wallet would be kind of weak. Especially when I'm temporarily imposing on other people's computers.

So I downloaded the appropriate iso, burned me a copy of ubuntu, slid over to linux.

I paused for a moment to be stunned at how much the desktop gui has evolved. Everything is snappier. Neater. More well organized. The way it automatically maximized space by putting the title bar in with the taskbar/menu bar thing kind of apple style was something that I used to spend several hours figuring out how to make happen back in 2008 or so. I'm super impressed. Dashboard is great. Everything is great. I'm getting another computer soon and can't wait to reacquaint myself with this OS after a long hiatus.

Anyway I downloaded UCK, which is an acronym for a program that guides you through the creation of a custom live-cd program, which sounded like just what I needed. However I've come to realize that this program simply was not made for running in a live-cd scenario. I kept running out of temporary-linux space or possibly (it was a vague error message) that I needed to have the cd that I intended to burn in the drive. Anyway several attempts to make this happen failed me.

I don't want to outright install linux on a computer that doesn't belong to me, for someone who has little interest in it, as it is a bit of a pain in the butt to remove, if I recall correctly.

The only solution I am able to come up with here is to run linux in a virtualbox in windows 7 and burn the cd in that, and any new partition that created wouldn't mess with my bootloader. Does this sound like it'll work to you guys? Am I even going about this right?

thinking about it further, I need to go in and figure out a way to change the place uck is putting trying to put the completed iso file...

hmm...

---

### Post by meteorrock on 2013-02-25
You can use Vmware with a linux on a USB or disk, I would stay away from mounting that linux or ubuntu build you want as a live distro, that is just for preview on a windows OS without virtualization.

Depends on what the hardware specs are on your "friends" computer, is it a laptop without much processing power or RAM? Virtualization like VMware works best on higher end computers.  Just use the direct .iso download without the "live" distro stuff. 

Bitcoins are a gamble, its only used in black market stuff on the deep web. Unless you know what you are doing, and I suspect you don't since you do not know how to use virtualization and linux, you are going to get raped by hackers. They love to exploit noobs. 

Do not mean to lecture you, if you want to make money online keep looking into how linux operates, lots of freelancer work for linux users online right now. Even for young people like myself.

---

### Post by merockstar on 2013-02-25
the problem im running into is i cant get uck to run off the live cd.

i was thinking if i installed linux for vmware, then used it to run uck, id be able to get the cd burned for regular use as a standalone wallet than boots into its own (ubuntu) OS.

Im not trying to run a live-cd os in vmware. im just thinking about trying to use vmware as an intermediary to get the cd burned without effecting someone else's bootloader.

figured id run it by you guys before i waste my time in case you could come up with a simpler solution, or u see a flaw in my plan.

as far as bitcoin itself ive already decided for my own reasons that its something i want to throw a little bit of cash at. im just trying to figure out a way to store them securely and thought an ubuntu live cd might be a good option.

---

### Post by merockstar on 2013-02-25
Ok i think this plan can work.

My only (admittedly paranoid) concern is that if there's any keyloggers running on the windows seven host, they'd be able to figure out the password I'm planning to use to generate my block-chain key thingy.

---

