---
title: "Returning To Ubuntu After A Decade - Need Directions Please"
date: 2023-10-29
forum: General Help
---

### Post by kinderfeld on 2023-10-29
Hey All,
Returning to Ubuntu after over a decade of having to use Windows. I haven't switched over just yet as there are a number of things I need to address first. Currently banging around with version 23.10.

I got some hardware issues I need to resolve before I can completely move back over. Most shouldnt be to hard and just need someone to point me in the right direction. Last version I ran was 10.something. So lots of changed and things dont feel nor look the same. 

Current hardware: i9-9900k, Gigabyte Z370 mobo, AMD RX-6800XT, 32 GB Corsair Veng DDR4-3200, MOTU M2 Audio and few various NVME/SSD/HDDs. Razer BW KB, Basilisk Mouse and Webcam. 

1st line of business is I need to find an application to control my Razer KB and Mouse lighting and button assignments. 
2nd is possibly controlling my Corsair Fans and Lighting using their controller. Though I can likely swap these out if need be.
3rd is Gaming, I mainly just play WoW so this shouldnt be an issue with Steam.

Those are my main 3 things. But if someone can also point in on how to get ubuntu desktop to quit putting new windows in the upper left side of my screen I would be most greatful as I have a 50 inch TV and its annoying.

Thanks, 
Joe

---

### Post by aljames2 on 2023-10-29
Welcome back!

You will likely want to hear from several here.  I can suggest a few things to consider as you begin to figure things out.  First I would start with using LTS versions, 22.04 being the latest long term supported version.  23.10 is more for those looking to help test for the future.  The next LTS will be 24.04

Next, have you considered installing Ubuntu in a VirtualBox VM to do some testing?  A good place to start.

For gaming, some play well in a VM, those that are less video card intensive. While it is possible to pass-through an extra GPU to a VM it is not easy & I wouldn&#8217;t even try it.

 Also, some games are windows only which means you would either need to use a VM if possible, or consider a dual boot setup for some &#8220;windows only&#8221; things.  Dual boot is also something I do not have experience with.  For my intensive games, I just have a separate windows metal box that I use for that.

---

### Post by kinderfeld on 2023-10-29
Thanks for replying. I am aware of Ubuntu release cycles and LTS support. I actually starting using Ubuntu back when 5.04 was released and ran Ubuntu for many years as well as Debian for a while. I used to compile many of the applications for 64bit for the community back when 32bit was still the main go to for most users. 

But however, the past 10-12 years Ubuntu and GNOME Desktop has really really changed. I cant say for the better, though STEAM looks promising. 

Currently so many things seem overly locked down and I am not a fan of that. I may end up seeing how SuSE and Fedora are looking with GNOME being less altered on them.

---

### Post by MAFoElffen on 2023-10-29
Welcome back!

I game to release stress. I've also been long time user of Ubuntu. I have Razor mouses, game pads and keyboards, their mouse pad... along with a Corsair Gaming Keyboard. Yes, I lost my sanity with that for awhile.

I really haven't found a Linux utility to switch the LED themes and lighting. But I dual boot, and set them in Windows to change the lighting of those. My other LED lighting is set in my BIOS.

Being I'm used to the Old UI, I still use more of a Gnome Desktop UI. I used to use the full gnome-ubuntu with gnome-desktop-flashback... Then I got used to Gnome3, and fell in love with it... But now I just add gnome-session, which is more lightweight, and doesn't include the full Gnome desktop suite. They started taking things away from the customization's abilities that we used to have in the older Gnome application UI's.

I still do a lot of theming tweaks to Plymouth Animations and the graphical login, the desktop... Some things have changed to keep doing that to things.

Steam still works good on either platform.

Being I've done dual-boot and NVidia since 2005, I just accept that Windows has an ego and breaks things in a dual-boot, that need fixing from time to time, and NVidia drivers still need to be re-installed occasionally to continue working.

Now my main gaming keyboard is a custom self-built RGB programmable compact 80 key, based on an ELF board, that my son convinced me to build. (He "collects" rare mechanical keyboards.) I have to say that it took some getting used to, but now... He was right. I'm "very" happy with it. I'm so used to it, that I have case for it to take it with me on my service calls! (LOL) I take the key-caps off and clean them about every 6 months. I've change the key-caps twice when I got bored on what they looked like. I also built a programmable gaming keypad.

---

### Post by TheFu on 2023-10-29
+1 for using Ubuntu. Steam tries to support Ubuntu as the main Linux based on my reading, but I'm not a gamer and would never load a tracking tool like Steam onto my network.
+1 for using the LTS.  Canonical has been using the non-LTS releases to try things that tend to fail since around 2012. Sometimes it is painful.  23.xx have been painful too.  Canonical's oppressive use of the default to try/inflict alpha-code onto a wide audience has been pretty bad. Best to avoid that.  

The only people who should choose a non-LTS at this point are people who need a really new kernel to support really new CPUs/motherboards (not you) and people who are testers.  I don't think Steam even attempts to support non-LTS Ubuntu releases.  [https://www.techradar.com/news/best-linux-distro-gaming](https://www.techradar.com/news/best-linux-distro-gaming) is from Sept 2023.  I don't know if TechRadar is a good review for gaming information.

The main things that Windows gamers do wrong on Linux are to assume getting GPU drivers directly from the vendor is a good idea. It isn't.  Stick with the GPU drivers provided through Canonical's installation tools for "propriety drivers".  **sudo ubuntu-drivers autoinstall** should handle it. There is a GUI in the "Additional Drivers" tool. I've never used it.  Avoiding nVidia generally means you won't have many issues with drivers.

I've only seen RGB, fan, and keyboard proprietary controls for Lenovo systems. Maybe something has changed?  My BIOS handles fan speeds for me, nothing in the OS involved. For keyboard shortcuts, I've been using built-in WM and xdotool. With Wayland, ydotool is the inferior replacement, such as it is.  xdotool only works with X11/xorg.

Wayland is a replacement for Xorg.  It is more secure and faster because it isn't network agnostic. It doesn't handle some things that long-time X11 users have come to depend on (like me). Nvidia + Wayland still have major issues.  I'd say, try using Wayland, see how it works for your needs.  If there are any issues, try Xorg and see if that fixes the problem.  In 2010, Wayland was just an idea because X11 is at least as ugly (poor security) as MSFT's entire desktop code.

Gnome has changed due to the entire Gnome team.  Canonical has a fetish with Gnome being like Apple's GUI. they tried to get Unity DE to be like it back in 2012 and inflicted that onto users for far too long.

After 2016, I stopped using any DE because they all felt too bloated. I'm back happily running the WM I used in 1995. It hasn't had any major changes since 2002-ish. It stays out of my way for being productive and I don't have to reset how I work every new release. YMMV.

---

### Post by kinderfeld on 2023-10-29
Ahh good ole WindowMaker. LOL my first distro was Slackware ver 7. Man I quickly learned how to compile everything back then. 

I loved Gnome2 and made many themes in the past. I swear the new Gnome devs keep stripping away more and more UI tools for the sake of being easier to use for new users. I get it, but kind of alienates the users that where brought up using Gnome2. Like myself. Though I am sure I can still change things, just have to find the text files with the theme settings. I did try KDE out tonight and thought it was going to be the way to go, but for some reason Plasma goes crazy when I use Wayland when outputting to my Samsung 50 inch TV I use as my main display. But Gnome compositing manager didnt have any issues when using Wayland. Sad. KDE used to be the GUI with the least customization, but now its the one with the most and better looking. But still ends up being as stable as a straw house in a hurricane. 

I did go back to the LTS version in hopes the documentation for most things will be more accurate and have less issues addressing my hardware concerns.

My 6800XT appears to be running correctly, though I havent bothered to try to run any games. But its detected and listed.
My CPU appears to also be running at my desired speeds at 5Ghz max. I have been having issues on Windows and having to use Intels overclocking utility for the past few years. But dont seem to have that issue on linux atm. 

Do you know the name of the software that allows remapping/macro-ing of keyboard and mouse key/buttons?

---

### Post by MAFoElffen on 2023-10-29
TheFu brought up a great point. 

I do DEV testing for the Dev releases. I am currently testing dev 24.04. I test every day. I expect there will be problems and things might not work. I come up with work-around's and file a whole lot of bugs. Some of my push on those, is that they need to be resolved before the LTS releases.

But my daily driver is still LTS. For a daily driver, I want and need "STABLE"! At least in that part of my life. For that, I currently run 22.04 HWE. On all my physical machines. Even my 10th through 13th Gen Intels. No problems with any new hardware.

I had more problems with my new 13th Gen on Windows!!! Ubuntu 22.04 LTS worked out-of-the box from the start gate. Windows 11 would not recognize over half the hardware without the motherboard vendor's Windows drivers. I had to use Linux to make that possible for me. That says "volumes".

I have to say that TheFu keeps at me, and he almost has me tempted to remove Windows altogether. (LOL) 

Linux is still customizable to whatever people want. If you do not like something, change it to your own preferences and needs. That is it's strength and weakness. There are so many choice open. Not all decisions with that, "Just because something is possible doesn't make it a good idea". I heard TheFu say that once, and have since adopted that. That is just so true.

---

### Post by #&amp;thj^% on 2023-10-29
> **MAFoElffen said:**
> 
I have to say that TheFu keeps at me, and he almost has me tempted to remove Windows altogether. (LOL) 


I'm going to second that, do you really use Windows any more?
Never Mind I forget you like to game on that.
Sorry Off Topic

---

### Post by aljames2 on 2023-10-29
> **1fallen said:**
> I'm going to second that, 

Same here.  TheFu taught me a ton starting out and still learning a lot, and also from the others on here.

When I switched to Linux, I really wanted to go cold turkey. Other than some games I payed at the time, there really wasn't much more that tied me to Windows. Since then, I've found a FLOSS solution to every productivity & hobby need, and I don't play games like I used to. I was tired of MS determining when I needed to upgrade my hardware, software, and when to open up the wallet again to pay up.  My gaming box is still there separate from everything else & that box is only started up when I get the itch to cramp up my fingers again playing a game, then it shuts down until next time.  No e-mail, no internet surfing, no banking, no bill paying, nothing on it but as I said.

---

### Post by dragonfly41 on 2023-10-29
> [COLOR=#000000]Do you know the name of the software that allows remapping/macro-ing of keyboard and mouse key/buttons?[/COLOR]

Do you mean tools like AutoKey, Actiona, xdotool for UI emulation?

---

### Post by TheFu on 2023-10-29
> **kinderfeld said:**
> Do you know the name of the software that allows remapping/macro-ing of keyboard and mouse key/buttons?

Answered in post #5.

---

### Post by MAFoElffen on 2023-10-29
ubuntu-session-flashback is the old Gnome2 theme... Just an idea.

The attachment is Dev Noble 24.04 on Gnome Session Flashback...

---

### Post by guiverc on 2023-10-29
> **kinderfeld said:**
> Hey All,
Returning to Ubuntu after over a decade of having to use Windows. I haven't switched over just yet as there are a number of things I need to address first. Currently banging around with version 23.10.


I noted a number of replies suggesting LTS; I'll add a case for keeping 23.10 here.

Ubuntu LTS *development* occurs over two years, starting just after completion of the prior LTS (ie. after Ubuntu 22.04 LTS was released). There are three *interim* releases which show the progress in that six month cycle (two years is broken into 4 six-month cycles), with the final release mostly just *polishing.* Ubuntu 24.04's *interim releases* were 22.10, 23.04 & 23.10 which you mention.

The Ubuntu 24.04 LTS when it's released, will be most like the 23.10 you already have, the *release-upgrade* 'taps' open for that release soon after 24.04 is released (*initially released for new installs*), with upgrades from 22.04 not *enabled* until **after** the release of 24.04.1.

You'll have an easier *release-upgrade* experience going to Ubuntu 24.04 LTS from the closer Ubuntu 23.10 release, thus that's one benefit of the Ubuntu 23.10.

Alas, many 3rd party software packages are built only for LTS, which is why many opt for the LTS releases, but benefits of LTS were already covered.

> **kinderfeld said:**
> 
I loved Gnome2 and made many themes in the past.

If you want a more traditional desktop experience,f maybe try Ubuntu MATE, or even Xubuntu. ie. you maybe happier with a [*flavor*]("https://ubuntu.com/download/flavours") with other  choices available too.

---

### Post by dragonfly41 on 2023-10-30
> OP: Do you know the name of the software that allows remapping/macro-ing of keyboard and mouse key/buttons?

TheFu: Answered in post #5.




Granted, @TheFu ... my weary eyes missed "xdotool"  in the small print.
But apparently it is fickle with Wayland.


but there are also ..
- Actiona (although rather old, new actions objects are expected in dev pipeline)
- pyautogui
- AutoKey

---

### Post by MAFoElffen on 2023-11-01
My shortlist for Linux Macro recorders / key remappers (Linux)
 - actiona (apt)
 - autokey-gtk (apt)
 - xdotool (apt)
 - input-remapper (apt)
 - kmonad (compiled from source)
 - keymapper (github, houman/keymapper)
 - keyd (github)
 - repeat (github)

LED Control Linux: OpenRGB

---

### Post by TheFu on 2023-11-01
Don't forget cnee and xnee.

---

### Post by dragonfly41 on 2023-11-01
Since I am interested in automation workflows (in toolchains) I consulted my "AI enabled PA" at [Phind.com]("http://phind.com")

Q1. In Ubuntu 20.04 what are the tools which meet this requirement: software that allows remapping/macro-ing of keyboard and mouse key/buttons?

Q2. Does Actiona meet this requirement?

Q3. Does cnee and xnee meet this requirement?

Q4. But there is a distinction between (a) emulating key presses as in Actiona and (b) recording key events. So can Actiona be used to orchestrate cnee and xnee and other UI tools?

Remember that often the AI/PA browser responses need to be challenged/corrected. And where a tool is unknown to the engine you point it to a url to be trained.

---

### Post by TheFu on 2023-11-01
For GUI automation, rather than looking at "automation" tools, look at software development testing tools.  After all, in these days of TDD (Test Driven Development), it is common to automate nearly all testing so that fully coverage including boundary conditions are always tested.  In many companies, the ratio of developers to tester is 1:3.  Creating test cases is another form of coding these days.  Seldom to testers manually point-n-click their test cases more than a few times before they code up a repeatable test case.

For example, when it comes to browser automatic testing, Selenium is what the professionals all use.  It does require some ugly setup, sadly.  I use SeleniumIDE for my browser automation. Alas, it is limited in that it cannot be used to press anything in the browser menu, just inside the main window ... sorta limited like an iframe would limit things.  Browser security doesn't allow saving files locally, so another tool needs to do that, which drastically slows the speed of automation allowed.

Imagine you need to visit 150 webpages that are dynamically created (different each day) and you want to save each page as text, not html for later processing.  The speed that each webpage becomes available is also dynamic from sub-second to perhaps 10 seconds - basically, the tool needs to recognize when the page is completely downloaded.
[https://AutomateTheBoringStuff.com/2e/chapter12/](https://AutomateTheBoringStuff.com/2e/chapter12/) is a little dated now, but the high-level ideas are there.  Javascript and Ajax get in the way too often, at least for my needs.

I had a system working well for years.  Then Wayland came and broke everything. Sigh.  Since then, I've had to insist on X11.  I've also improved the peripheral processing, but the core copy/paste from each webpage is still the sticking point.

---

### Post by dragonfly41 on 2023-11-01
I am thinking through not so much testing but the scenario where (say) a Jupyter Notebook runs a kernel code (or poly kernels) which can takeover desktop operations through CLI.
The ugly interface with [YouTube]("https://ubuntuforums.org/ROOT--YouTube_216.html") screenshots (which have to be copied and pasted) comes to mind. I prefer to load commands into say desktop Yakuake and then run them (bearing in mind security awareness of hostile actors).
So it is the interaction of pushed eLearning modules (browser presentations) with the desktop environment that is of interest.
Cutting out all the [YouTube]("https://ubuntuforums.org/ROOT--YouTube_216.html") stuff, often with commentary in different dialogues, while you are listening and hoping to catch the screenshots which often I (for one) cannot easily read.
Selenium I know about but I have also tried Sikulix long ago.
[http://www.sikulix.com/](http://www.sikulix.com/)
[https://sikulix.github.io/docs/](https://sikulix.github.io/docs/)
Consider trying to teach a remote user to navigate a complex desktop application or workflow. sans YouTube.
To use a simple tool like Actiona we first grab coordinates of key targets, place then as vars in javascript array and set off the workflow.
Such training modules might be held in a repository and for security hashed to ensure they are not tampered with (which is another story).

---

### Post by TheFu on 2023-11-01
> **dragonfly41 said:**
> 
Consider trying to teach a remote user to navigate a complex desktop application or workflow. sans YouTube.


Back in the mid-1990s, we just added **TCL** to our applications and had all the clients (50+) connect to our teaching server to get follow-along commands.  I didn't do this coding, but a guy on the team did and it took him just a few hours to completely make the GUI commands from the teacher's workstation go to all the students. Of course, we were all on the LAN Unix-only LAN, air-gapped from the internet.  [https://tcl.tk/doc/integration.html](https://tcl.tk/doc/integration.html)  TCL can seem odd to people who have never used it.

These days, if there's internet, I'd just use _meet.jit.si_ (or another free Jitsi server - there are a bunch) and start a shared room for the shared window/desktop I wanted, then let all the people who were supposed to attend know the URL.  Any WebRTC capable browser can join.  There are android apps and AppImages with using Electron (yuck!) for the people who want a self-contained, single file, setup. No signup/login needed for anyone other than the first user to open the room.  I think Jitsi decided to force the first person to use some cloudy-service login for authentication due to some abuses (IDK), I just show up to these meetings a few minutes late to do my presentations, so someone else "opens" the room.  There are already enough security issues with WebRTC, but it seems the world has decided it is the web conferencing protocol/method of choice now.

Just providing options, since I've never had luck with ActionA or similar tools.  

Today I found a perl module that can control firefox, so I may be able to better automate one of my dynamic workflows.  [https://metacpan.org/pod/Firefox%3A%3AMarionette](https://metacpan.org/pod/Firefox%3A%3AMarionette) - we shall see how long that lasts, if I can get it working.   Won't know until I try.  The older [https://metacpan.org/pod/WWW::Mechanize::Firefox](https://metacpan.org/pod/WWW::Mechanize::Firefox) broke when Mozilla changed their software in 2017. WWW::Mechanize is a cornerstone for Perl people doing web automation.

Automating non-browser stuff isn't hard. There's usually a CLI tool which does 80% more than the GUI provides anyway.  Most GUI programs only provide 20% of the functionality ... though for simple use, that is almost always more than sufficient.  It is just hard for a repeatable process to happen when humans are point-n-clicking stuff. We are forgetful animals.

---

### Post by MAFoElffen on 2023-11-02
For that: JitBit, atbswp, and Actiona... nThere is actually more doc's, videos and tutorials on how to use JitBit, and atbswp, than on ActionA. 

Selenium is good for automating the testing of websites and web-based applications. It has some very good browser hooks.

---

### Post by Claus7 on 2023-11-02
Hello,

> **kinderfeld said:**
> ...But if someone can also point in on how to get ubuntu desktop to quit putting new windows in the upper left side of my screen I would be most greatful as I have a 50 inch TV and its annoying.
...

if I'm not mistaken, I suppose that you use ubuntu under wayland. In order to avoid seeing new windows opening on the top left hand side of screen, then you should install gnome-tweaks under synaptic and from there go to Windows and enable the option Center New Windows.

Regards!

---

### Post by TheFu on 2023-11-02
> **MAFoElffen said:**
> For that: JitBit, atbswp, and Actiona... nThere is actually more doc's, videos and tutorials on how to use JitBit, and atbswp, than on ActionA. 

Selenium is good for automating the testing of websites and web-based applications. It has some very good browser hooks.

JitBit is commercial.
atbswp only works with Xorg/X11, may as well use cnee, which has been around 20+ yrs.
```
# To record (1 second delay to get windows and mouse placed).   This records absolute mouse movements and all keyboard presses until the 'q':
$ cnee -t 1 -rec --first-last --keyboard --mouse -o SavedActions.xms -sk q
# Press 'q' to end save.

# To playback, 
$ cnee -rep --synchronised-replay  -f  SavedActions.xms
```

The problem with xnee/cnee is that if the mouse is used, it is positional, so the click points need to be the same from run to run to run. It doesn't know about underlying "objects".  

That's why Selenium is so good.  It captures the object and "clicks" on it - no worry about position, but sometimes objects change.  I ended up writing some perl to snag a current webpage, then find all the objects to be pressed, then generate a SelenuimIDE script as the output for that perl script.  I did use SelenuimIDE to record the initial script, but when the underlying website objects all shifted, that all broke down.  Alas, SelenuimIDE won't save/append webpages to a file.

ActionA uses Javascript.  Just shoot me in the head already.  I've avoided knowing too much JS for 25 yrs. ;)  

Selenium is fairly complex due to the client/server architecture.  Really need a 2 week class on how to setup and use it OR a mentor who can help.

---

### Post by MAFoElffen on 2023-11-02
@TheFu -- I have to admit, I have never used xnee/cnee. Maybe I should explore using them.

I am not opposed to buying commercial software if it is worth it. Being I am a disabled veteran, and having health issues recently... I am on a fixed budget, which makes me watch my finances closely. That sometimes makes me appear cheap, and frugal about most things. But I am also not a masochist.

---

### Post by dragonfly41 on 2023-11-03
> [COLOR=#000000]ActionA uses Javascript. Just shoot me in the head already. I've avoided knowing too much JS for 25 yrs. [/COLOR]:wink:

[COLOR=#000000]Selenium is fairly complex due to the client/server architecture. Really need a 2 week class on how to setup and use it OR a mentor who can help.[/COLOR][COLOR=#000000]

TheFu, to be fair Selenium also uses Javascript and has its issues. Read the mixed reviews.
Since your challenge project posted above is quite relevant to broader need to a automate scraping and analyse a corpus of multiple url's (some with fleeting or sub-second views as you mention) and to extract text (using BeautifulSoup or other)  I will apply some spare time (partly for my own needs in training) to build a demonstrator based on Actiona (eLearning container), Selenium, Sikulix et al.  Sometimes more agile tools can meet the requirements without extensions.

Probably to post later in a new thread subject to commitments.[/COLOR]

---

### Post by TheFu on 2023-11-03
I'll be checking out [https://metacpan.org/pod/Firefox::Marionette](https://metacpan.org/pod/Firefox::Marionette) when life gives me free time to get into this.  I played with it yesterday, but was unable to figure out selecting the "id" from 150 of the input files.  If I know the specific ID, it is easy, but I need to find the unique CSS ID values and simulate a mouse click onto those objects as the loop control.   I already have another way to get a list of the ID values in perl (basically an ugly regex), but wanted to use the Firefox::Marionette module to loop over each of them in 1 statement from the DOM.  Once I figure that out, it shouldn't be hard to drop use of SeleniumIDE completely.  The lack of Firefox::Marionette clear examples with HTML inputs is my problem.  They show specific code, but don't show the source HTML which applies to that code.  Sigh.

Firefox::Marionette isn't included in 20.04 perl modules, but it is in 22.04, which I haven't moved into.  On 20.04, there are some dependency issues that I haven't researched for loading the module into a virtual perl environment. I use perlbrew to keep my perl projects separated from the OS perl stuff whenever possible.

---

### Post by dragonfly41 on 2023-11-03
TheFu I wil throw one fast ball to you.
Are you aware of the Wolfram Engine to extract data from URL's?

[https://blog.wolfram.com/2018/03/02/web-scraping-with-the-wolfram-language-part-1-importing-and-interpreting/](https://blog.wolfram.com/2018/03/02/web-scraping-with-the-wolfram-language-part-1-importing-and-interpreting/)

I am starting to research twinning this engine with LLM's. That is grabbing text as training corpora.

There is a free general tool WolframAlpha.com to understand capability, but the full power comes from the Mathematica engine.

The little tool Actiona (earlier) can be used to populate the query fields in Wolfram UI.
But going further you could use Jupyter Notebook to run kernels.

---

### Post by TheFu on 2023-11-03
Lots of good ideas ... perhaps for others.

I'm anti-cloud and not interested in tying anymore of my workflow to external tools that absolutely necessary.  Wolfram is out for that reason.  I don't want to use cloudy processing.

Funny, their example of grabbing NOAA data is something I solved long ago using curl + grep + sed. I don't need detailed data. Just the forecast from a reputable source that I'm already paying to use (via taxes) that won't track and sell my data.

```
curl --silent --show-error --user-agent '.' --header '' --location --connect-timeout 15 --max-time 15 "https://forecast.weather.gov/MapClick.php?lat=$LAT&lon=$LON&unit=0&lg=english&FcstType=text&TextType=1" | \
    egrep -i "today|tomorrow|This Afternoon|Tonight|${TOMORROW}" | \
    sed "s/<[^>]*>//g; s/&\|;/ /g; s/\r/junk/; s/$year/$year\n/; s/Issued by/, Issued by/; s/Last Update/, Last Update/; s/ deg /°/g; s/(Text-Only)//; s/Advisory/Advisory /g; s/Warning/Warning /g; s/Watch/Watch /g; s/: / - /g;"

```
Assuming I fixed the spacing and newlines correctly.  There are a few variables that need to be filled in first - LAT, LON, TOMORROW. year.

Some of the other tools above use Java. I'm not a fan.

Tried to learn python, but keep getting frustrated over their indentation mandates.  If I were new to programming or a little more flexible, perhaps Python would work for me, but I'm over 30yr programming and have a specific indentation style that conflicts with Python.  I'm a big boy and know what I like my code too look like.  Code that doesn't have semicolons to end a statement just looks wrong to me.

So many of my constraints are self-imposed due to the languages that other people choose.  I avoid php, javascript, python, java and anything with DotNET (or whatever they are calling it these days).  I prefer perl, go, C/C++. With those choices, nearly anything is possible.  Perl has a huge library of verified, continuously tested, cross-platform modules that was the envy of every other language for decades.  Entrance to the library requires providing test cases and a sufficient number of supported platforms. Plus, because people think that perl is hard, only those willing to actually learn the language bother, which creates higher quality code because the barrier to learning is higher than javascript or python or php.

My goal with my little project is to completely automate some workflows. It was completely automated a few years ago, but then some external providers changed and my efforts to reuse other people's solutions failed.  At this point, nearly everything is automated, except there's some manual processing that takes about 5 minutes every week left to be automated.  I'll spend a few days creating the code with Firefox::Marionette .  After I learn the simple stuff, automating all sorts of web stuff will be 100x faster (coding time) and not be the barrier it is currently.  I'd love to be able to use WWW::Mechanize which is historically how web automation was handled, but it doesn't support javascript. There was a WWW::Firefox (or something like that) which was a subclass of Mechanize and worked well, but Mozilla decided to change some things.  I don't know if the new or old way is better. They are just incompatible.

---

### Post by dragonfly41 on 2023-11-03
Wolfram kernel runs in desktop or cloud .. but never mind.

I did find a route to convert Perl to other languages.
I was interested in Perl to HaXe which is available.
That is a jumpimg point to other languages.
[https://www.codeconvert.ai/perl-to-haxe-converter](https://www.codeconvert.ai/perl-to-haxe-converter)

[HaXe]("https://haxe.org") in turn can compile into other languages.
So the flash of an idea is you can write in familiar Perl and popout [HaXe]("https://ubuntuforums.org/ROOT--head--greensock--DrawSVGPlugin--concatenate_process--workflow--resources--HaXe_56.html") code.


But returning to my AI PA Phind.com I am becoming familiar with (I have just subscribed having experimented for a while to become familar and learn) I asked the question:

> query: How to automate Firefox Marionette with Perl for scanning URLs
second query: How to extract text and CSS ID from a webpage using Firefox Marionette and Perl



This comes up with a workflow. If you do not want to train Phind with your questions you need a subscription.

P.S. my coding experience started 60 years ago .. perhaps earlier if we include analogue computing.

---

