---
title: "Firefox /tmp directory problem"
date: 2022-08-21
forum: General Help
---

### Post by 0cs935-bill on 2022-08-21
Just upgraded to 22.04.1 LTS which installs the snap Firefox.

I have a script that runs Firefox periodically all day to pop up messages. The URL is **file:///tmp/Message.html** where the script writes the contents of that file as necessary. I discovered that any reference to the real **/tmp** get directed to  **/tmp/snap.firefox/tmp** and then Firefox display a file not found. If I move MESSAGE.html to my home directory Firefox executes it just fine. What's the deal with Firefox not understanding the real **/tmp** ?

---

### Post by &amp;KyT$0P# on 2022-08-22
Are you able to use the [official Mozilla build]("https://www.mozilla.org/firefox/all/#product-desktop-release") of Firefox for Linux 64-bit instead of the snap?

---

### Post by SeijiSensei on 2022-08-22
/tmp is readable and writable by anyone. What about /tmp/snap.firefox/tmp? Does it look like this:
```
$ ls -l / | grep tmp
drwxrwxrwt  20 root root 12288 Aug 22 07:39 tmp

```
That "t" on the end references the "sticky bit." On a directory, the [sticky permission]("https://en.wikipedia.org/wiki/File-system_permissions#Permissions") prevents users from renaming, moving or deleting contained files owned by users other than themselves, even if they have write permission to the directory. (Numerically, the sticky bit is set using the leading digit in the octal representation, 1777 for a world-writable directory like /tmp.

---

### Post by 0cs935-bill on 2022-08-22
I'm trying to avoid tinkering with the install. I'm a retired professional software developer and could compile from source if necessary, but I have better things to do. This seems like it has to do with fencing off the application for security reasons and someone hosed up the logic somewhere. If others can replicate this behavior then it should be a bug and the developers should fix it. If it's some kind of "feature" then it's just stupid. I've already worked around the problem. I bring it to the attention of the forum to highlight what might be a bug.

---

### Post by 0cs935-bill on 2022-08-22
I don't care about and don't want to disturb [COLOR=#000000]/tmp/snap.firefox/tmp[/COLOR] in any way. That's Firefox's area of control and I don't want to mess with it at all. Till this occurred, I didn't know that area existed. I'd just like Firefox to process my input as I intended, namely bring up the perfectly useable html file located at the system's /tmp. 

I'd like to know if others can replicate the failure. Put some html file at /tmp and tell Firefox to process it via file:///tmp/whatever.html . If multiple people see this then it's a bug and I'll bug report it.

---

### Post by TheFu on 2022-08-22
Snaps are constrained and only allowed write access to specific directories, as determined by the snap development team and, with some extra settings, the snap packager team.  /tmp/ isn't one of those locations.  If your HOME directory isn't under /home/, the useraccount isn't allowed to run snaps at all.

If you want to have control over where programs can write on the file system, don't use snap packages. That's the harsh truth.
[https://snapcraft.io/blog/a-technical-comparison-between-snaps-and-debs](https://snapcraft.io/blog/a-technical-comparison-between-snaps-and-debs)
and
[https://forum.snapcraft.io/t/accessing-tmp-from-snaps/22384](https://forum.snapcraft.io/t/accessing-tmp-from-snaps/22384)  in short, forgetaboutit.

---

### Post by SeijiSensei on 2022-08-22
Follow the steps here to remove the snap, add the Mozilla PPA to your sources list, and get normal .deb versions that aren't constrained like snaps.

[https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)

---

### Post by Paddy Landau on 2022-08-22
> **0cs935-bill said:**
> The URL is **file:///tmp/Message.html** …
As others have said, that's a security restriction by snap.

**EDIT: My snap solution seems not to work :(**

You have several options, but I think that the easiest by far is perhaps to simply move the file to
/tmp/snap.firefox/tmp/Message.html
That will solve that!

Another option, maybe just as easy, is to use your Cache folder:
~/.cache/Message.html

If you don't wish to do either of those, you could try using the DEB as already suggested.
____________

Or, try using the flatpak version, which is less restricted than snap, and whose security can be tailored with Flatseal. (If you need to know how to put flatpak onto your Ubuntu system, ask, and I'll give you the instructions. They're straightforward.)

---

### Post by grahammechanical on 2022-08-22
One of the advantages (or in your case, disadvantages) of snap packaged applications is that the application is not allowed to access system folders. The /tmp folder is a system folder and as you have noticed the standard (deb packaged) version of Firefox can access system folders. Is it not a security risk to allow applications to access system folders? Is not the web browser a vector for malicious code to access the OS?

I have seen several posts on this forum advising users who are running an OS that is not receiving any security fixes to not access the internet. It seems that security protection from malicious code entering from the internet is important except when that protection is provided by a method of software packaging that is called Snap packaging. Or, is Canonical the target here?

> **Snaps** are Linux app packages for **desktop**, **cloud** and **IoT** that are simple to install, secure, cross-platform, and dependency-free.

They **update automatically** and typically run within a **confined** and **transaction-based** environment. **Security and robustness** are their key features, alongside being **easy to install**, **easy to maintain** and **easy to upgrade**.


[https://snapcraft.io/docs](https://snapcraft.io/docs)

> **Sandboxed applications**: one of Flatpak&#8217;s main goals is to increase the security of desktop systems by isolating applications from one another. This is achieved using sandboxing and means that, by default, applications that are run with Flatpak have limited access to the host environment.

[https://docs.flatpak.org/en/latest/introduction.html#reasons-to-use-flatpak](https://docs.flatpak.org/en/latest/introduction.html#reasons-to-use-flatpak)

Does the Flatpak packaged version of Firefox allow the user to access system folders? 

Regards

---

### Post by &amp;KyT$0P# on 2022-08-22
> **grahammechanical said:**
> It seems that security protection from malicious code entering from the internet is important except when that protection is provided by a method of software packaging that is called Snap packaging. Or, is Canonical the target here?

No.  The problem you're seeing is the result of snap packages not allowing the *user* to choose *their own* security.  Different people need different levels of and different types of security for their different systems.  What would be security measures on one user's system, could be solely obstructive on another user's system.

One-size-fits-all security **does not exist**.

> Does the Flatpak packaged version of Firefox allow the user to access system folders?

Looks like not by default -
```
$ flatpak install flathub org.mozilla.firefox
Looking for matches…

org.mozilla.firefox permissions:
    ipc                   network               cups                    pcsc
    pulseaudio            wayland               x11                     devices
    file access [1]       dbus access [2]       bus ownership [3]       system dbus access [4]

    [1] xdg-download
    [2] org.a11y.Bus, org.freedesktop.FileManager1, org.freedesktop.Notifications,
        org.freedesktop.ScreenSaver, org.gnome.SessionManager, org.gtk.vfs.*
    [3] org.mozilla.firefox.*, org.mozilla.firefox_beta.*, org.mpris.MediaPlayer2.firefox.*
    [4] org.freedesktop.NetworkManager



```
You would have to explicitly set it up to access system files if you want that.

---

### Post by 0cs935-bill on 2022-08-23
For some reason, I'm not subscribed to the topic I initiated so I haven't gotten any notifications of replies. I looked around to see how to subscribe to this topic but failed. My profile says to email me immediately on replies but that didn't happen because I'm not subscribed.

I worked around this issue by placing my file at my home directory and then nuking the file at the end of the script right after I pull Firefox down. The /tmp usage was just a convenient place to store temporary files that automatically get cleaned up on a reboot.

I figured that part of this issue was security based fencing of the application. However, converting my request for the OS's **/tmp** shouldn't be converted to the application's **/tmp/snap.firefox/tmp** and then tell me that my file doesn't exist when it does. I filed a bug report with Mozilla about this conversion behavior.

As for nuking the snap and replacing it, I figure that the developers are forcing more and more to snap and therefore any avoidance is a short term strategy. I'm not certain of what the internals to snaps look like but I suspect that they statically link everything they need to run the app in the snap package so they completely control the environment it runs in. No more dynamically linking to an O/S supplied library that isn't compatible somehow. This cuts down on problems and lowers support hours spent on things they don't have direct control over. I get it.

I hated the snaps in V20 because they were agonizingly slow. I see now that the speed issue has been fixed so my previous objection to snaps has been solved. I also understand the developers implementing security but don't like the idea of that security focus breaking things that worked previously. 

I also filed another bug report against Firefox when I noticed that Firefox wasn't honoring their **--new-window**, **--new-tab**, **--new-instance** and **--private-window** command line arguments. I discovered this while trying to come up with a work around for the /tmp issue.

---

### Post by TheFu on 2022-08-23
Snaps might be pushed by Canonical, but not by anyone else.  Hopefully, they will die off like Unity DE did and hopefully, it won't take so many years as Canonical inflicts their NIH syndrome on everyone else.

Firefox is a available and works as you need, just not packaged as a snap.  There have been lots and lots of similar issues and each has been closed with "working as designed." I wouldn't hold your breath.

Some parts of snaps are statically linked, but not all.  There are specific core libraries that are also provided as snap packages (adding more bloat) which are used by other snaps.  If this sounds familiar, it is because that's the point of shared libraries.  Canonical has re-invented that wheel.

I greatly appreciate that you've opened two bugs against firefox. Please keep going. It can't hurt.  The firefox snap breaks all sorts of workflows.  One of the issues with snaps that is a "won't fix" is that users without HOME under /home/ aren't supported.  That makes snaps nearly useless for enterprise customers.

---

### Post by 0cs935-bill on 2022-08-23
I was a development manager for a mainframe software house decades ago. We statically linked our products (sold for $30,000 to over $200,000 back then) because we wanted complete control over which libraries were used. We didn't want to reinvent the wheel, but we did want to have a wheel that was a known quantity. That provided us with isolation to operating system changes that had newer versions of the same libraries we used. Over time, we would recompile and link with the newer libraries once we tested our products with those libraries and again statically linked in a stable version to avoid issues. 

I think that's where snaps are going. The distributed app is larger because it contains library code that might be identical to what's already on the system, but it's the isolation and reduced tech support calls that allowed us to concentrate on improving the products as opposed to chasing down compatibility errors that just pissed off customers. Snaps also reduce the tech support load on Canonical because they didn't package the app, the experts for the app did. If there's an app problem, the app developers know that there's an incredibly high likelihood that it is their problem and not some O/S issue. This further reduces bug resolution time, labor and cost.

I've got more horsepower, RAM and disk space than I know what to do with and it's all dirt cheap so having some app bloat with redundant code isn't an issue. Avoiding dynamic system library calls also makes apps faster at execution time, something everyone appreciates. 

Statically linked apps have many advantages for the developers and for the O/S suppliers. I think Canonical may be ahead of the curve on snaps. As the snap architecture improves as is already evident on V22 LTS versus V20LTS, there's an ever greater case to be made by the developers and O/S suppliers to go the snap route.

---

### Post by Paddy Landau on 2022-08-23
> **0cs935-bill said:**
> … I think that's where snaps are going.
That's exactly where snap is going.

What I don't understand is why Canonical doesn't just use Flatpak. It already exists, it already works well, and it even has Flatseal (or the equivalent CLI commands) to fix security problems like the OP's. What a waste of resources from Canonical!

---

### Post by 0cs935-bill on 2022-08-23
Paddy: I haven't investigate Flatpak or what it's intended to do, but you've piqued my interest so I now have another project. 

I see you have an "ubuntu member" designation besides your ID. What does that signify?

---

### Post by TheFu on 2022-08-23
> **0cs935-bill said:**
> I was a development manager for a mainframe software house decades ago.  

I was a software developer, lead, application architect, enterprise architect and still code for a living, sometimes.  Programmed on MVS/TSO, 20+ Unixen, Windows, OSX, Linux and AS400 over all those years, but spent most time as a cross-platform developer at a small company where everyone wore many hats.

For many people, running Linux on their older hardware is how they begin.  Lots of people have old chromebooks with 16GB of storage, so having 10G of that storage used by 10 snap packages isn't really an option.

Any real software development team creates scripts to build their packages.  I did.  Every build, which was for each platform, usually 2-3 times a week, wasn't complete until the person assigned created the full install/upgrade packages for each platform.  That was all automated, except for MS-Windows; damn you InstallShield!  InstallShield required a human to point-n-click to create packages back then.
Further, the guy making the packages was responsible for running a new install on every platform (around 6) and upgrading the team's test DBs on those 6 platforms. Then that person would update the build documentation, since breaking the build was heavily penalized.  Once guy was so bad at it that he was suck doing all builds, on all platforms for 3 weeks.  As the dev lead, I felt it was important for every developer to cross-train and know how to do the builds and packaging for each platform, so we could all go on vacation for 3-6 weeks without leaving the team screwed. Some people didn't appreciate that.  We had a few libraries (dynamically loaded plugins) where only 1 person knew how to build and install them.  When that 1 person wasn't available, which happened a few times, the company was forced to make a difficult choice.

QA would accept each build and run their automatic tests on all 6 platforms, along with testing for the 'niche' issues that only a skilled human with a "knack" for testing would come up with.  There are testing geniuses in this world.

Mozilla isn't going to be able to fix the /tmp/ issue.  While the do seem to care about bloat, they don't care nearly enough, IMHO.  Working on embedded systems in by first job taught me how important being efficient with the available bits of RAM was. We weren't allowed to malloc() anything.  All the memory storage locations were known for everything in each mode. That was a safety thing, so we could remotely patch specific locations without risk that those would be different from run-to-run.

There is always a trade-off between security, convenience, and capability.  The flatpak team seems to have the right mix.  The snap team is over the line with restrictions.  One size doesn't fit everyone.

BTW, snaps don't run everywhere, even in normal environments.  For me, on systems that aren't using LDAP nor HOME directories outside /home/, only about 20% of the snaps I've tried actually work.  They are missing needed libraries. This seems more common with Qt stuff, but it also happens with GTK+ stuff, from time to time.

---

### Post by Paddy Landau on 2022-08-23
> **0cs935-bill said:**
> Paddy: I haven't investigate Flatpak or what it's intended to do, but you've piqued my interest so I now have another project.
Flatpak does exactly as snap does, but it's more flexible. [Official website]("https://flatpak.org/"), and the [Flathub store]("https://flathub.org/").

If you're using Ubuntu 20.04 or 22.04 (I haven't tested any others), you can integrate Flatpak into your system including the Software Store.

[LIST=1]
[*]Install gnome-software as a dependency.
```
sudo apt install gnome-software-plugin-snap gnome-software-plugin-flatpak
```
[*]Remove the now-redundant Ubuntu Software Store.
```
snap remove --purge snap-store
```
[*]Start "Software" (which is gnome-software). This is the Gnome Software Store, which looks almost the same as the Ubuntu Software Store that it replaces.
[*]Menu > Update Preferences > turn on automatic updates and notifications.
[*]Restart your computer (I'm not kidding; this step is important).
[*]Add the Flatpak store, i.e. Flathub.
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
[*]Use "Software" to install Flatseal and Extension Manager. (The very first time you search for software, it might take a minute as it populates from Flathub, but thereafter it works normally.)
[/LIST]
From now on, use your system normally. When you want to install a package from "Software", at the top right, you'll be given a number of choices depending on what's available.

Or, of course, you can use the CLI: apt, snap or flatpak.

Use Flatseal (or the CLI) when you need to tweak the security permissions for a package.
[LIST]
[*][Sandbox permissions]("https://docs.flatpak.org/en/latest/sandbox-permissions.html")
[*][Sandbox reference]("https://docs.flatpak.org/en/latest/sandbox-permissions-reference.html")
[*]Basic [YouTube explanation]("https://youtu.be/iOtYEqxPSHE").
[/LIST]
> **0cs935-bill said:**
> I see you have an "ubuntu member" designation besides your ID. What does that signify?
Some time ago, when I was deeply involved as a volunteer with this forum and other parts of Ubuntu until illness forced me to cease, I applied for Ubuntu membership. I needed it to be able to create and edit community help pages (I have made a few). That's pretty much all that it means.

---

### Post by 0cs935-bill on 2022-08-23
Maybe it's snap, maybe it's flatpak or maybe it's something else. The idea of encapsulating applications code as much as possible is decades old and is a good idea. To migrate from the current environment to one where applications are fenced off from the O/S as much as possible isn't going to happen in one step, but that appears to be the desired direction, so I'm not going to fight it. The inconveniences along the way are lamentable but are to be expected. 

I was on Caldera Linux when I started investigating an alternative to Novell Netware and Microsoft Windows networking environments. I even installed 3COM Ethershare for a while. I ended up on Fedora from FC2 through FC28 till I bought an app (BricsCAD) that didn't like Fedora and Ubuntu was the recommended O/S. While on Fedora, I experimented with SELinux and it wasn't ready for prime time but the direction for fencing off processes from the O/S perspective was clear and also a good idea.

---

### Post by 0cs935-bill on 2022-08-23
Paddy: Thanks for the overview. I'll check things out.

Would anything from the flatpak environment give me back something that resembles the much better V20 user interface? This constantly hitting the Windows key is a PITA. Not being able to drag and drop an app from one workspace onto another is a step backwards. On V20, I used to be able to just highlight text and scroll click it into somewhere else and now I have to go through the extra steps to purposely copy and then paste. It's annoying and certainly no improvement in usability.

---

### Post by Paddy Landau on 2022-08-23
> **0cs935-bill said:**
> The idea of encapsulating applications code as much as possible is decades old and is a good idea.
In the days when RAM and storage were frighteningly expensive, it was a bad idea! In some ways, it's still not a good idea, because it prevents reusability. However, the pros (especially sandboxing) are greater than the cons, now that RAM is plentiful, and storage is cheap.
> **0cs935-bill said:**
> To migrate from the current environment to one where applications are fenced off from the O/S as much as possible isn't going to happen in one step…
Well, Android and iOS have (mostly) succeeded in this. I think that it's merely a matter of time. I wonder if Microsoft is intending something similar in its Windows Store?
> **0cs935-bill said:**
> Would anything from the flatpak environment give me back something that resembles the much better V20 user interface?
I'm sorry, I have no idea what a V20 interface is.

A flatpak app works exactly the same as a DEB or snap app, whether it's CLI or GUI. The only noticeable differences are security, and how you call it.

DEB: gimp
Snap: /snap/bin/gimp
Flatpak: flatpak run org.gimp.GIMP

As you can see, Flatpak is less convenient from the CLI, but you typically have menu entries, or you can use keyboard shortcuts. I have no non-GUI flatpaks installed, but if I did, I'd just make a shortcut or alias for it.

Now, I have no idea if I've come anywhere close to answering your question, sorry! Please ask again if you meant something different. I searched for "v20 interface" but found nothing useful.

---

### Post by TheFu on 2022-08-23
There are 20 different DEs.  Each has strengths and weaknesses.  Try a few.  

The default DE on "Ubuntu Desktop" 20.04 was Gnome3.  22.04 is Gnome4.  There are KDE, LXQt, Mate, Cinnamon, and lots of other DEs that are worth looking.  Or you can use no DE - and just a MW.  Many WMs provide the non-bloated GUI you may like, but since GUI taste is always subjective, nobody else can decide for you.  A 5 min video on each DE might be worth looking at to get to a short list to try.  Then try each on your own system.  I would recommend 

Unix, DOS, and MS-Windows systems have been keeping library dependencies separate for decades. Simple management of LD_LIBRARY_PATH is all that is needed.  AppImages do this for non-technical users.  AppImages are like flatpaks or snaps, but without the constraints or work-flow breakage.

---

### Post by 0cs935-bill on 2022-08-23
Paddy: I was referring to the stock Ubuntu V20 LTS GUI environment as opposed to the stock V22 LTS GUI. The V20 GUI was less cumbersome to use.

---

### Post by 0cs935-bill on 2022-08-23
TheFu:  A few years ago I tried KDE and a few others but went back to Gnome because at that time Gnome still had the best all around environment for my taste. I was hoping for some tweaks that would allow me to stick with Gnome but give me back the better usability that the older version has. This Windows button usage is a real turn off.

---

### Post by Paddy Landau on 2022-08-23
> **0cs935-bill said:**
> Paddy: I was referring to the stock Ubuntu V20 LTS GUI environment&#8230;
Ah. Ubuntu versions always have a dot. The past few ones were 20.04, 20.10, 21.04, 21.10, and now 22.04.

The first number indicates the year of release, and the second the month of release. So, 22.04 was released April 2022. LTS versions are even-numbered and end in .04, i.e. April in every even-numbered year. They also have names like Jammy Jellyfish, but that's just confusing!

I presume, from your comments, that you are using 22.04.

I don't have a problem with mouse-wheel copy (I forget the technical name for it). I wonder what's changed in your environment?

Are you aware that you can log in with either the newer Wayland or the older X.Org? When you get to your login screen in 22.04, once you've selected your name but before you type your password, select the cogwheel at the far bottom-right of your screen. There, you can select either "Ubuntu" for Wayland (the default), or "Ubuntu on Xorg" for X.Org. They appear identical, but there are some small differences. Try X.Org to see if it works better for you.

I am confused by your references to the Windows button (which is called the "Super" key in Linux). What causes you to have to keep pressing it?

---

### Post by TheFu on 2022-08-23
> **0cs935-bill said:**
> TheFu:  A few years ago I tried KDE and a few others but went back to Gnome because at that time Gnome still had the best all around environment for my taste. I was hoping for some tweaks that would allow me to stick with Gnome but give me back the better usability that the older version has. This Windows button usage is a real turn off.

I completely understand.  I use fvwm, which provides more control over how the GUI behaves, but it isn't really for point-n-click people. Configuration and customization is through text config files.  Whenever we see modern space movies and they show a computer screen, it is likely fvwm providing the GUI.  Plus, fvwm is 20x lighter than any DE.
[https://www.linuxjournal.com/article/1236](https://www.linuxjournal.com/article/1236)   Plus, fvwm has been development stable for 15+ yrs, so we aren't at the whim of some GUI team confusing "new" with "better."

Just another option, plus using fvwm will save 200MB-1GB of RAM use compared to other options.

But it is non-stock, which many people would consider a negative.

---

### Post by 0cs935-bill on 2022-08-23
Paddy: It didn't occur to me to check which windowing system I was on. I was on Ubuntu (Wayland). What threw me off was that under V20.04, Wayland wouldn't work for one of the utilities I had so I always worked on X11. When I booted up on V22.04, that utility worked, so I assumed I was on X11 when I wasn't.

I am now on "Gnome" and I got most of the environment I like back. No more Windows / Super key. 

Thank you for the hint on where to look.

---

### Post by Paddy Landau on 2022-08-24
> **0cs935-bill said:**
> I am now on "Gnome" and I got most of the environment I like back.
Wayland and X.Org are *protocols*.
GNOME (GNU Network Object Model Environment) is the *desktop environment* (DE).

Ubuntu 20.04 and 22.04 both use the GNOME DE.

 Ubuntu 20.04 uses the X.Org protocol; Ubuntu 22.04 allows you to choose whether to use the Wayland or X.Org protocol.

So, you would have been on GNOME all along, unless you *manually* changed the DE.

Wayland still has some pending problems that are being worked on. For the most part, they aren't a problem, but sometimes they are. For me, I have to use X.Org for some of my automation. For you, Wayland causes a problem with your mouse actions. (It's probably due to security. Wayland is more secure against certain types of malware than the much older X.Org, which is why Ubuntu is transitioning to Wayland; but that can prevent certain insecure features from working.)

So, I'm glad that you resolved your problems!

---

### Post by TheFu on 2022-08-24
Wayland and nvidia GPUs haven't gotten along recently.  In 22.04, Canonical actually would setup X11 on systems with nvidia GPUs to avoid the issue - I think that happened about 2 weeks after the initial release.

Wayland breaks many of my workflows too, so I'm using X11 as well.  I get the feeling they will never be able to correct some of those issues due to the added security, unless they make some specific optional settings to allow other programs full access to the Wayland communications.  Hopefully, the Wayland team would be such purists like some other teams (cough) are with not compromising and allowing local control over some necessary things.

---

### Post by Paddy Landau on 2022-08-24
> **TheFu said:**
> Hopefully, the Wayland team would be such purists like some other teams (cough) are with not compromising and allowing local control over some necessary things.
I hope so. It would be a pain to lose the automation that is possible with X.Org.

---

### Post by 0cs935-bill on 2022-08-24
My box has a mobo intel video chip as well as an add in Nvidia Quadro P400 that has 3 ports. My two monitors (one exclusively used for 3D CAD) are attached to the P400 board and the upgrade from V20 to V22 apparently read the unused intel video chip of just defaulted to Wayland because I got the Wayland default at login. When I switched over to the X11 at login, I got most of the environment I wanted. The application icons are now at the bottom of the screen instead of the left and I hope they'll offer an option in some future release to put it back on the left.

Whatever the developers did to the system in V22, my CAD package (BricsCAD) is now lightning fast compared to V20 by an order of magnitude for a Zoom. I was planning on building a new box with a faster CPU chip but now I don't have to.:P

---

### Post by tea for one on 2022-08-24
> **0cs935-bill said:**
> The application icons are now at the bottom of the screen instead of the left and I hope they'll offer an option in some future release to put it back on the left.
Are you referring to the Dock?
Settings > Appearance > Dock > Position on screen.

---

### Post by 0cs935-bill on 2022-08-24
tea for one: I believe that's what it's called, the Dock.

There is no "Appearance" in my Settings application. I logged in via the "Gnome" list item when I hit the gear on the login screen. I noticed different Settings options when I logged in via the "Ubuntu" login option. 

This is one area where Linux and Gnome in particular has seriously messed up when it comes to user friendly configuration year after year after year. The controls are all over the place. Some in Settings, some in Tweaks, some in Configuration Editor, some in dconf Editor, some via a web app, on and on. The Gnome shell extension descriptions are too cryptic to be of much value, for example. Other controls provide very poor documentation for what they are intended to control. The other day I tried looking for Gnome themes and was greeted with a web site with lousy organization and where the individual theme pages were so poorly documented that one has to try each one to see what you're going to get. Linux documentation is easily one of the worst features of the system.

---

### Post by Paddy Landau on 2022-08-24
> **0cs935-bill said:**
> There is no "Appearance" in my Settings application.
I'm wondering if you really do have Ubuntu 22.04.

The cogwheel at the login screen is only to swap between Wayland and X.Org.

Once you have logged on, move your mouse to the very top-right of your screen, and click. From the mini-menu that appears, select *Settings*. In the window that opens, select *Appearance*. On the right, scroll down to *Dock* >*Position on screen* > *Left*.

---

### Post by 0cs935-bill on 2022-08-24
Here's my Setting menu of options:

---

### Post by 0cs935-bill on 2022-08-24
I found what looks like the proper key/value pair in dconf Editor and changed 'BOTTOM' to 'LEFT', rebooted and it didn't change anything. 
I double checked in dconf Editor after the reboot and it says 'LEFT' but the dock is still at the bottom.

---

### Post by Paddy Landau on 2022-08-25
> **0cs935-bill said:**
> Here's my Setting menu of options:
How odd… You are missing your Appearance setting! (See attached screenshot.)

I don't know what to say about that, other than start a new thread asking for help with this.
> **0cs935-bill said:**
> I found what looks like the proper key/value pair in dconf Editor and changed 'BOTTOM' to 'LEFT', rebooted and it didn't change anything. 
I double checked in dconf Editor after the reboot and it says 'LEFT' but the dock is still at the bottom.
That is the correct key, but can you put LEFT without the quotation marks?

---

### Post by tea for one on 2022-08-25
As Paddy says, your settings are incomplete.

Can you open a terminal and run:-
```
apt show ubuntu-settings
```
```
edited@edited-22-04:~$ apt show ubuntu-settings
Package: ubuntu-settings
Version: [COLOR="#0000FF"]22.04.6[/COLOR]
Priority: optional
Section: x11
Origin: Ubuntu
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 41.0 kB
Depends: dconf-gsettings-backend | gsettings-backend, gnome-control-center-data, gsettings-desktop-schemas (>= 40), libglib2.0-bin (>= 2.53.4-3ubuntu1~)
Task: ubuntu-desktop-minimal, ubuntu-desktop, ubuntukylin-desktop
Download-Size: 6,508 B
APT-Manual-Installed: no
APT-Sources: http://gb.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
Description: default settings for the Ubuntu desktop
 This package contains the default settings used by Ubuntu.
edited@edited-22-04:~$ 
```

When you upgraded to 22.04, was this an in-situ upgrade or a clean installation using the Ubuntu 22.04 ISO?

---

### Post by 0cs935-bill on 2022-08-25
I can't key in anything. All I can do is pick a word like 'LEFT'.

This was done in-situ.

---

### Post by Paddy Landau on 2022-08-25
> **0cs935-bill said:**
> I can't key in anything. All I can do is pick a word like 'LEFT'.
I see. In that case, you've done the right thing. But something is definitely amiss.

What are the results from *tea for one*'s suggestion [FONT=courier new]apt show ubuntu-settings[/FONT] and the question about how you installed 22.04?

---

### Post by 0cs935-bill on 2022-08-25
I guess you missed it. I stated the move to V22.04.1 was done in-situ. 

I compared my output to tea for one's version and the output is identical. 
bill@bill ~$ apt show ubuntu-settings
Package: ubuntu-settings
Version: 22.04.6
Priority: optional
Section: x11
Origin: Ubuntu
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 41.0 kB
Depends: dconf-gsettings-backend | gsettings-backend, gnome-control-center-data, gsettings-desktop-schemas (>= 40), libglib2.0-bin (>= 2.53.4-3ubuntu1~)
Task: ubuntu-desktop-minimal, ubuntu-desktop, ubuntukylin-desktop
Download-Size: 6,508 B
APT-Manual-Installed: no
APT-Sources: [http://hn.archive.ubuntu.com/ubuntu](http://hn.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
Description: default settings for the Ubuntu desktop
 This package contains the default settings used by Ubuntu.


**I'm going to bug report this.**


BTW - I read up on Flatpak and installed it. I discovered that the executable for Firefox is now firefox-bin and it lives in a directory path that's likely to change from patch to patch with no reliable way to call it from the command line rendering it problematic for script use. Admittedly few will need this but I was relying on it to pop up messages initiated from my crontab setup. I've since written a python app to do the popups. 

/var/lib/flatpak/app/org.mozilla.firefox/x86_64/stable/53dfa2353e5dea4790484feab30c09b28391d4fe30f71352c6854f51f359aa54/files/lib/firefox/firefox-bin



There should be a link maintained by the flatpak mechanism that would allow the app to be referenced conveniently from within scripts. The call sequence inside the firefox .desktop file is Greek to me as it somehow relies on some flatpak infrastructure for proper execution.

---

### Post by Paddy Landau on 2022-08-25
Don't call the executable directly.

The correct way to call a flatpak app is like this:
```
flatpak run org.mozilla.firefox
```
If you don't know the parameter to use, issue this command:
```
flatpak list
```
It shows all the installed apps. Firefox's looks like this:
```
Firefox         **org.mozilla.firefox**   104.0    stable system
```

---

### Post by tea for one on 2022-08-25
Very odd to see your settings window is missing the Appearance option yet the package is correct?
I imagine that you cannot even choose Light or Dark theme style?

I wonder if the in-situ upgrade completed correctly?

Can you navigate to /usr/share/themes and see if all the Yaru themes (i.e. 10 colour choices) are installed?

---

### Post by 0cs935-bill on 2022-08-25
Paddy: Thanks for the education. I guess I need to do more reading to figure out where all the knobs and switches, brakes and gas pedal are.

BTW - I reported the Setting app issue (1987665) and in the process of using ubuntu-bug I got a complete lock up inside Chrome when I selected an image file to upload. Tried it again and it locked up again immediately after attempting to attach an image. Did it again without attempting to attach an image and that took.

Tried to do another bug report on ubuntu-bug. Come to find out you can't do an ubuntu-bug on ubuntu-bug itself so I added the ubuntu-bug mechanism failure report on the end of 1987665. 

Thanks for all your help.

---

### Post by 0cs935-bill on 2022-08-25
tea for one: The in-situ upgrade worked as expected, to the best of my knowledge. I saw no errors. Everything I normally use is working perfectly and my 3D CAD app now feels like it has a 1000 horsepower engine. The improvement in graphics zooming in and out on a complex drawing is an order of magnitude faster than under a fully patched V20.04LTS .

 bill@bill ~$ ll /usr/share/themestotal 122880
drwxr-xr-x 4 root root ? 4096 Aug 21 12:26 Adwaita
drwxr-xr-x 4 root root ? 4096 Aug 21 12:26 Adwaita-dark
drwxr-xr-x 4 root root ? 4096 Jul 31  2020 Default
drwxr-xr-x 4 root root ? 4096 Jul 31  2020 Emacs
drwxr-xr-x 4 root root ? 4096 Aug 21 12:26 HighContrast
drwxr-xr-x 3 root root ? 4096 Jul 31  2020 Raleigh
drwxr-xr-x 7 root root ? 4096 Aug 21 12:29 Yaru
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-bark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-bark-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-blue
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-blue-dark
drwxr-xr-x 7 root root ? 4096 Aug 21 12:29 Yaru-dark
drwxr-xr-x 3 root root ? 4096 Aug 21 12:29 Yaru-dark-hdpi
drwxr-xr-x 3 root root ? 4096 Aug 21 12:29 Yaru-dark-xhdpi
drwxr-xr-x 3 root root ? 4096 Aug 21 12:29 Yaru-hdpi
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-magenta
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-magenta-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-olive
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-olive-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-prussiangreen
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-prussiangreen-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-purple
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-purple-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-red
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-red-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-sage
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-sage-dark
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-viridian
drwxr-xr-x 5 root root ? 4096 Aug 21 12:29 Yaru-viridian-dark
drwxr-xr-x 3 root root ? 4096 Aug 21 12:29 Yaru-xhdpi

My bug report on the Setting issue is 1987665 .

---

### Post by Paddy Landau on 2022-08-25
> **0cs935-bill said:**
> … I got a complete lock up inside Chrome when I selected an image file to upload.
I've not had a problem with this.

I'm starting to suspect that the problem lies in your installation, specifically that something went wrong. Unless other people have the same problem as yours, your [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1987665") might go nowhere.

I'm going to upgrade my main computer from 20.04 to 22.04, but I'll be doing a fresh installation. (My current 22.04 was also a fresh installation.) I generally find that fresh installations are cleaner. Provided that you have a fully working, tested backup, in my experience, it doesn't take much longer than an upgrade in situ.

---

### Post by 0cs935-bill on 2022-08-25
Paddy: I **never** did O/S in-situ upgrades until I purchased ($1500) a 3D CAD app (BricsCAD) that is very finicky about its environment. BricsCAD got me to migrate from Fedora to Ubuntu because it wouldn't run right on Fedora. I was on Fedora from FC2 through FC28, a very long time. That app requires an authorization process that ties a key to the app so it will run on a particular box as an anti piracy measure. The last time I untied the key from the box to render the app useless before I nuked the box and installed from scratch, I spent days with the apps tech support trying to reinstall the app AND tie the key to it. 

I was dreading migrating to a new hardware setup because the app was so slow while zooming as my drawings got more and more complex, but I couldn't stand it any more. I had already picked out all the components to build a new box with a CPU twice as powerful as the one I'm currently using. On a completely separate topic, I was investigating a software project that required LibreOffice 7 that was conveniently available by upgrading to V22LTS so I decided to do the upgrade only to discover to my delight that CAD zooming is now fixed. I don't have to spend the money AND I don't have to go through the potential pain of reinstalling the CAD app and its nuisance lock.

If I knew I could install BricsCAD and the lock on a nuked clean box, I'd do that in a minute as that's been my preferred approach since I started on Caldera Linux way back when Ray Norda ran it. I knew Ray from my Novell Gold reseller days.

---

### Post by Paddy Landau on 2022-08-25
Hmm, in that case, I can understand that you'd want to leave well alone!

Might I suggest that you start a new thread asking about your dock and the missing settings, and post a link here so that we can find it. Mention that you upgraded from 20.04 to 22.04, because that might be important, and include the results from [FONT=courier new]apt show ubuntu-settings[/FONT].

---

### Post by 0cs935-bill on 2022-08-25
[https://ubuntuforums.org/showthread.php?t=2478396&p=14109671#post14109671](https://ubuntuforums.org/showthread.php?t=2478396&p=14109671#post14109671)

---

