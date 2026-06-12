---
title: "Two questions from a shell noob"
date: 2021-11-18
forum: General Help
---

### Post by martinkeat on 2021-11-18
Morning Folks,

So I have finally come over to the dark size and am phasing out my windows machines in favour of linux. Trying my hand at writing my first shell script and I could do with a pointer or two in the right direction. I have two specific questions.

[B]Question one

[/B]Obviously in the shell script you put each command on a different line as you go. Now from what I can see there's no issue with most commands related to sudo apt install... in terms of manual intervention because sticking a -y argument in there simply skips over the prompts and it assumes that permission is given to proceed. My first question is on how to deal with packages which require manual intervention i.e. installing a different desktop interface. 

How exactly do I get the shell script to wait until the manual intervention is done and (in this case) the different desktop interface is installed before it moves onto the next command on the list.

[B]Question two.

[/B]There are obviously points in a script where you might need to do a reboot with the sudo reboot command, so my second question is if there is any way to have the shell script reboot the computer, and then launch in to the next command when it starts back up.


Thanks ahead of time for your replies.

Martin

---

### Post by sudodus on 2021-11-18
1. A typical command that you use in the shellscript will wait for your manual intervention. And the shellscript will wait for the command to finish (unless *you* put it into background with a **&** character at the end of the line).

There are exceptions, commands that go into background by themselves, but do not worry about that now.

2. You are talking about advanced scripting now. Yes, that is possible. One way would be to make a cron job. Probably you need elevated permissions, so use

```

sudo crontab -e

```

or use 'autostart', associate a desktop file to your script and put the desktop file into the 'autostart' directory of your user ID.

Those things are somewhat complicated for a beginner. There are good tutorials that you find via the internet.

[hr][/hr]
X. Please start with small and simple scripts, and step up gradually to more advanced scripting.

Y. It is probably easiest to really help you, if you ask about specific problems, that you want to solve. There are so many tools and methods, that you can apply instead of inventing the wheel again, and often someone here can help you find a tool, that is useful for the problem that you want to solve.

Z. Last but not least, try to get rid of the Windows mindset, and be open to the Linux way to do things.

---

### Post by dragonfly41 on 2021-11-18
> Question two.

There are many ways of orchestrating commands for more advanced scripting.
Too numerous to list.
But you should focus first on learning solo commands.
Explore other terminals such as Yakuake.


Coming from the &#8220;dark side&#8221; as you write you will be familiar with AutoHotKey.
That is, &#8220;UI automation&#8221;.

Now in Ubuntu there is a similar tool, which although quite dated and using Actionscript2 and QT4 objects, I find very useful. Its name in Actiona.

sudo apt install actiona

Here you have a GUI which allows libraries of commands to be run. It is similar to an old Ubuntu tool clicompanion (which used Python 2 and is no longer in use). But there is an upgrade somewhere which uses Python 3.

Another useful tool is Albert where you can write your own Python extensions to run commands.

Yet another approach is running Ansible scripts.

And another is to run commands within Python scripts using subprocess.

And so it goes on.  Basically I now keep a library of commands and use a frontend GUI such as Actiona  to run them
and customise arguments through dialogue boxes. This approach can be used in cloud services such as google cli.

[P.S.] I forgot to mention Jupyter Notebooks and Jupyter Lab which I am using more and more.
Jupyter allows multiple kernels to be run in sequence so you might use the Bash kernel for running a command or script then in the next cell you might switch to another kernels such as Python. In between "input cells" (commands and scripts) you can write markdown notes which are not executed, so you keep all your "polyglot" workflow in notebooks. This is the most comprehensive framework I have found.

[P.P.S.] And finally I must add [webmin custom commands]("https://doxfer.webmin.com/Webmin/Custom_Commands").  webmin runs as a localhost server on port 10000.

There are other methods but that's the list I have tried.

---

### Post by TheFu on 2021-11-18
For systems management, ansible is the step AFTER you attempt to create your own using whatever shell programming language you like.  It usually takes about 6-12 months to realize that the ansible guys were smart and created more maintainable tools than your beginner-level bash scripts.  Ansible has an idea of parallelization.  You can do that with your scripts too, but there is lots of detail management necessary.  Ansible should tell APT that it is running in batch mode, so no questions are allowed. You'll just end up with incomplete configuration for a few packages.  It is up to you to either provide the required settings (probably using either a file or template through ansible's capabilities) or to manually come back and run the reconfigure option with dpkg.

In general, I avoid putting sudo inside an script.  If a script needs to run with elevated privilege, then I put a check at the top to verify the uid is 0.  It is possible for root NOT to be the userid, but the uid must be 0.

Whenever creating scripts that shouldn't be interactive, just provide the required inputs for each command. Typically there will be an input-file option or a command will accept input from stdin ... which can be provided using redirection or piped input from some other command.  This is very common.  The Art of the Command Line (google it) has an entire section on redirection. Very worthwhile reading - and put it on your calendar to re-read each year, since in 12 months your deeper understanding will make stuff you don't understand today click.  As more and more parts fit, your understanding becomes deeper and deeper and deeper over the decades. Let us know when you've reached Wizard level. ;)

Lots of people seem to want to automate full patching.  I'd warn you against doing that. I've been burned and left with a system that removed the DBMS and left the system useless due to a bad dependency in a package.  Whatever you do, be certain you log the script and review those logs ASAP to find any issues.   Don't get me wrong. I have a script to patch my systems weekly, but it gets run manually and it logs everything. It isn't very pretty, but works for the 5-25 systems I've had here over the decades.  For patching, I found ansible overkill, but for many other needs, it is exactly the right tool for the right job.

Ansible ... Puppet ... Chef ... CFengine ... Rexify ... SaltStack are all similar "DevOPS" tools.  I've looked at them all - really wanted Rexify to be the best since I'm a perl developer, but Ansible was the right mix of capability while being as simple as possible.  Many of the tools were causing just as many problems as they claimed to solved.  I attended training on Puppet and Chef ... both use Ruby as their underlying language and I love ruby!  Alas, Ansible is just so much cleaner and doesn't add unneeded complexity.  In the Puppet class, they pointed out that people were using Ansible to create the dynamic list of systems for Puppet to send commands.  Ansible, Puppet, Chef skills are all in very high demand today.  Ansible is agent-less, unlike the others (besides Rexify). That's a big deal to me.  Ansible is a "push" architecture, whereas Puppet and Chef are "pull" architectures.

There are lots of beginning shell scripting guides.  Google "**Beginning bash scripting guide**" for the LDP one. [https://tldp.org/LDP/Bash-Beginners-Guide/html/](https://tldp.org/LDP/Bash-Beginners-Guide/html/)  They also have an "**Advanced Bash Scripting Guide**" ... ABSG which I find is very useful.  

However, whenever any bash script becomes longer than 1 page, I switch to a different language with better features, modular programming support and a huge library of pre-tested tools.  mcpan is amazing. Nearly anything I can need has already been created, tested, made cross-platform, and is maintained. I bet python has something similar.  Ansible has a shared solutions area too, so we can take the work of others which has been improved on over the last 10 yrs into a great solution.  

For example, it is common for people to deploy nginx using ansible.  It typically has a few steps.
* install the nginx package
* open the firewall 80/tcp and 443/tcp ports
* tell systemd to startup nginx after boot

Inside a company, we might want to limit the external firewall on the nginx box to only allow a few specific subnets on our LAN, not every office in the company and definitely not the external world. Making that the default for internal ansible nginx deployments might be good, with a specific task/roll to open the firewall a little more for corporate-wide access.  When you have hundreds or many thousands of servers, automation is important not just to constantly improve things, but to capture knowledge by experts that come and go in the company in the form of ansible scripts with comments.  Plus, if there is a huge bug in some software and we need to ensure our public-facing servers are patched ASAP, ansible is a great way to both do the patch, but also to report that the patch has actually been applied.  Accurate reporting on these things is almost more important than the actual patch - at least to upper management.

Sorry - I went off on a tangent.

---

