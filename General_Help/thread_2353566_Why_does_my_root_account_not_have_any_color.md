---
title: "Why does my root account not have any color?"
date: 2017-02-22
forum: General Help
---

### Post by rufflechip on 2017-02-22
ubuntu server 16.04.1 LTS

Why does my root account not have any color?  I notice the user1 account I created has color & the below type ls command yields these different results.



root@abc:/$ type ls
ls is hashed (/bin/ls)

vs.


user1@abc:/$ type ls
ls is aliased to `ls --color=auto'

How can I return? the root account to having color?  I'm not sure if it came this way or if there is a reason for it not to have color?

Thanks!

---

### Post by QIII on 2017-02-22
Are you using SSH in to the server or are you using I/O devices and a monitor attached to the server?

Why on Earth are you logging in to your server as root?

---

### Post by DuckHook on 2017-02-22
> **QIII said:**
> &#8230;Why on Earth are you logging in to your server as root?Darn&#8230; you just beat me to asking this same question.

---

### Post by lisati on 2017-02-22
> **DuckHook said:**
> Darn… you just beat me to asking this same question.

Same here.

---

### Post by cariboo on 2017-02-23
Add the following alias to root's .bashrc

```
alias ls='ls --color=auto'
```

Having run as root many, many years ago, it is possible to make a big enough mistake, that you need to do a re-install.

---

### Post by ajgreeny on 2017-02-23
Interestingly, on my desktop machine, not a server, I always edit the /root/.bashrc file to make sure that root's terminal prompt is coloured red as a warning to make me fully aware that I am using root terminal, and I add a few of my useful user aliases as well, for the few times that I use root terminal.

Always backup the .bashrc file before editing it as you could cause BIG problems if you get it wrong!

---

### Post by DuckHook on 2017-02-23
@aj

Might I respectfully ask you to share the relevant bits of your /root/.bashrc? It would help a lot of people&#8212;me included!

---

### Post by 1clue on 2017-02-23
IMO the best part of Ubuntu is that they disable the root user.

That said, I frequently login as someone else and 'become root' for a short time rather than put sudo in front of everything.

In my opinion, the things you put in /root/.bashrc need to be filtered through the idea that this is the account you fix things with when everything else is broken. This account MUST work. So I limit my changes to things which do one of the following:
[LIST=1]
[*]Inform me that I am logged in as root.
[*]Aid me in performing the very limited types of tasks that I perform as root.
[*]Make it more difficult to do normal things an root, so long as that doesn't interfere with doing the things I need to do quickly and correctly.
[/LIST]
 
Another thing I try to make sure of is that when I'm acting directly as root, the console should plainly state that I am root.  I ensure that if the user is root then the PS1 prompt states [COLOR=#ff0000]root[/COLOR][COLOR=#000000]@[/COLOR][COLOR=#000000][/COLOR][COLOR=#008000]hostname:[/COLOR][COLOR=#ffa500]/my/current/path[/COLOR][COLOR=#000000]. Normally the username is a different color than red.

Historically for security reasons, '.' and '~/bin' do not appear in root's PATH. I strongly advise against putting them in there as then root may inadvertently run an unsafe app or script. Also root typically runs /bin/sh which is more limited than /bin/bash.
[/COLOR]
Ubuntu has blurred the lines somewhat, but typically root's PATH is "/bin;/sbin;/usr/sbin;/usr/bin". On other distros I still enforce this policy as it helps focus the root user's task on only those things a system administrator might need to do as root.

---

### Post by DuckHook on 2017-02-23
@OP

If you are still following all of this, all of the above is good advice, but it breaks down as follows:

[LIST=1]
[*]To colourize your output, do as cariboo suggests in post #11 above.
[*]The bigger issue, however, is the use of root, which is disabled in Ubuntu by default.
[*]Most of us have invoked a root shell at some point. On very rare occasions, it is just more convenient than typing in sudo every ten minutes.
[*]But, like Cariboo, it has caused me computing disaster in the past.
[*]Frankly, I think it a bad habit, notwithstanding that this will likely elicit a whole bunch of blowback from gurus and gentoo/arch/slackware types who play in the root account all the time.
[*]In Ubuntu, it is not necessary to enable the root account. If you want a root shell, do:```
sudo -i
```…and you have one until you exit out of it.
[*]I still think it a good idea to have your root prompt as alarming a shade of colour as you can find, so I hope ajgreeny posts his .bashrc snippet.
[/LIST]

---

### Post by rufflechip on 2017-02-23
Hi:

Wow, a lot of responses & all are greatly appreciated.  I think I mis-typed previously.  I am logging in as the original login & using sudo.  I'm not actually "bypassing" sudo & acting as an old style unix root user.

With that in mind, I think I'm being advised to change this user's .bashrc file as follows:
[COLOR=#000000]

[/COLOR]alias ls='ls --color=auto'[COLOR=#000000]
Did I cause this to be different?  I thought I did the exact same install on another machine & the first (original) user has the color coding. . .

Is it possible that I inadvertently changed my .bashrc file?   I know I didn't sudo nano into it, I only created this build in the last 2 weeks.

When I get home I will post my .bashrc file if that would still be helpful.

Thanks,
newbie

[/COLOR]

---

### Post by 1clue on 2017-02-23
You didn't cause it to be different. That's how it is by default.

---

### Post by 1clue on 2017-02-23
Oh yeah @DuckHook,

About "gurus" blowback on root user.  I don't know if I'd be called a guru or not, I've been using Linux exclusively on my desktop since 1996 but there are definitely people who know a lot more about it than I do. And I use Gentoo as my other favorite distro, so I guess your comment hits on multiple levels.

Most of the people I see warning others about using root account are the people who have been around the longest, and probably most or all of those have one or more personal horror stories to tell. My personal biggest disaster as root user cost the company I worked for many thousands of dollars in downtime. It was a combination of a regular expression acting in an unanticipated fashion and having root permissions that seriously messed up a system which was key to the company's financial workings. While I had "scrape it off and start over" events before that as a consequence of being root at the wrong time, that was the one that convinced me.

I think that it's not just the long-term root scenario where you need to be careful.  I've had incidents using sudo in a pipe as well, really it's not significantly different than having done my entire pipe as root. You just need to be careful when you have elevated permissions. There are very few things you need to do with permissions greater than those of a normal user.

---

### Post by ajgreeny on 2017-02-23
OK folks; here's the edit I make to /root/.bashrc (lines 36 - 57 but might be different line numbers in yours, so just look for this section) to get the change to prompt colours.
I have to remove the comment from my own user .bashrc to get the green prompt as well; Ubuntu does not appear to give us that by default.

I have shown the specific lines changed from default in red below to help you.
The first simply removed the comment # from the line start in order to get a coloured prompt, the second changes the number 32 (green) to 31 (red) but you can make changes to other colours if you wish; the colour codes are shown below but I have not experimented any further.

Below are the color init strings for the basic file types. A color init
string consists of one or more of the following numeric codes:
Attribute codes:
00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
Text color codes:
30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
Background color codes:
40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

Make sure you backup the /root/.bashrc first just in case something goes wrong with ```
sudo cp /root/.bashrc /root/.bashrc-backup
``` then edit the /root/.bashrc with ```
sudo nano /root/.bashrc
```

```
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
[COLOR="#FF0000"]force_color_prompt=yes[/COLOR]

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;[COLOR="#FF0000"]31[/COLOR]m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt
```

---

### Post by JKyleOKC on 2017-02-23
> **rufflechip said:**
> With that in mind, I think I'm being advised to change [COLOR="#FF0000"]this user's[/COLOR] .bashrc fileThe thing that nobody seems to have brought up yet is that "sudo" actually launches a subprocess as "root", and thus uses the configuration files in the /root directory rather than your own (which is how I'm interpreting your reference to "this user" above).

The black background that results is just the default for the root user; making the changes others suggest will change it. I heartily second the suggestions to make the prompt itself quite glaring, because it's easy to forget where you are, and a single typo can easily result in wiping everything out when you run as root, even with sudo!

---

### Post by DuckHook on 2017-02-23
> **1clue said:**
> &#8230;While I had "scrape it off and start over" events before that as a consequence of being root at the wrong time, that was the one that convinced me&#8230;There are very few things you need to do with permissions greater than those of a normal user.
Not that the OP needs any more convincing, but I just couldn't resist:

My clutching-throat screaming-in-agony moment occurred when I first started using Linux. At that time, I was a Windows power-user with an oversized ego and almost capsizing with lousy XP habits. None of this "limited privileges" nonsense for me. After all, I was a Big Bad "Power User".

Had two terminal windows open. One was running as mighty root in /. The other was my disrespected, measly, piddly, "powerless" user in a temporary directory I was using to transfer files. I had just learned the Linux command line and to clean out the temp directory, I did rm -rf and&#8212;without a second glance&#8212;<Enter>.

I don't even need to tell you what happened next&#8212;window focus was on the wrong window. Something that innocuous. That simple. Thirty seconds later, I finally realized that I had wiped out all of my photos, videos, e-mails, financial data&#8230; being a "Power User" also meant that I was too cool and invincible to bother with backups.

Luckily for me, Mrs DuckHook is the infinitely understanding sort. It also helped that I shelled out a few hundred bucks for the professionals to recover some of that data.

---

### Post by cariboo on 2017-02-23
Thanks ajgreeny, for the tip.

---

### Post by DuckHook on 2017-02-23
Yes, thanks ajgreeny!

…I don't know why system didn't notify me of your post… :confused:

It's very useful and will be implemented immediately.

---

### Post by ajgreeny on 2017-02-24
I'm very happy you think this is worthwhile; it is a very minor and simple thing to do, but it does on occasion bring me up short when I'm using the command line, letting me know immediately, with just a quick glance which account is open in terminal.

When I started using Linux full time 12 years ago with Ubuntu 5.04 or 5.10, I kept away from the command line as much as I could, largely from fear, but once I started to use it for simple things I soon became comfortable using it for more complicated activities, and I no longer have any fear of it.

I will however, repeat the mantra; BACKUP - BACKUP - BACKUP, before playing around with system files or you might regret it!

---

