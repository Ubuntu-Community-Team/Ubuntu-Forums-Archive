---
title: "Create a GUI on a headless server"
date: 2014-12-30
forum: General Help
---

### Post by mrJTparadise on 2014-12-30
Hey everyone,

I'd like some advice on the creation of a GUI.

I have a headless Ubuntu 14.04 server that hosts a variety of services and my goal is to create a GUI that interacts with the services offered.  The GUI would live either on the server or a separate client would dial in to the server and access it that way.  I already have the communication ( server/client ) architecture in place so that isn't a concern.

I know I could install some desktop environment (gnome, unity, etc) and create my GUI that way but I am wanting to keep the headless server, well, headless (no gui).

I have looked into GTK+, Qt, and even perl and python with their additional modules and it looks like they require to have a desktop environment.  I obviously have some options but if there is anyone out there that has experience doing something similiar to this any advice would be greatly appreciated. 

Happy holidays,
JT

---

### Post by dragonfly41 on 2014-12-30
webmin might meet your requirements ...

[http://www.webmin.com/](http://www.webmin.com/)

webmin is in Ubuntu repo so you can install on the headless server and manage services via web.

---

### Post by mrJTparadise on 2014-12-30
webmin looks more like a web based system admin utility.  I need something I can develop.

---

### Post by dragonfly41 on 2014-12-31
> my goal is to create a GUI that interacts with the services offered

It might help responders if you give an example of a client/server interaction which currently available tools do not offer
and so you need to develop a GUI.

---

### Post by mrJTparadise on 2015-01-02
Sorry.  I am looking for suggestions and recommendations because I am not familiar with the currently available tools.

I am running a headless server that has it's own commands that returns specifics such as temperature and voltages.  I wanted to create a GUI for this rather than have a user use the command line.  I also want to keep the headless server.  So for instance, the user may go full command line or if wanted, type a command to bring a up a GUI.

---

### Post by dragonfly41 on 2015-01-02
Would you wish to have the headless server _push_ a stream of changing voltages, temperatures and other changing data ... to a community of users .. rather than have users _poll_ the headless server services via SSH tunnel?

if push streaming data is your preference then take a look at [http://www.pusher.com](http://www.pusher.com) (which I only recently learned about).

Tutorial here ... [http://code.tutsplus.com/tutorials/getting-real-time-with-pusher--net-22106](http://code.tutsplus.com/tutorials/getting-real-time-with-pusher--net-22106)

...

For any client side GUI I suggest installing Quickly and Glade on your development platform for quick development of Ubuntu apps.

e.g. using Quickly I'm developing a GUI widget to run on client to interact with headless server to manage workflows.

*Note: There are other ways .. such as here ..*

[http://askubuntu.com/questions/425371/how-to-run-gui-applications-remotely-on-a-headless-server](http://askubuntu.com/questions/425371/how-to-run-gui-applications-remotely-on-a-headless-server)

However .. back to client side GUI development.

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

Quickly can be installed via Ubuntu Software Centre on development platform.  Also you need to install Python Glade.

Whilst in Ubuntu Software Centre you can install Synaptic Package Manager.

Now .. launch Applications > System Tools > Administration > Synaptic Package Manager .. search "quickly"

This is what I have installed on Ubuntu 14.04 ...

quickly
python-quickly-common
python-quickly-core
quickly-ubuntu-template
quickly-community-templates-common
quickly-ubuntu-application-qt-template
quickly-ubuntu-application-qtquick-template
quickly-ubuntu-html-app-template

...

My Quickly templates are installed in

/usr/share/quickly/templates

they are ..

ubuntu-application
ubuntu-application-qt
ubuntu-application-qtquick
ubuntu-cli
ubuntu-flash-game
ubuntu-html-app
unity-lens


Additional templates can be found here ...

[https://launchpad.net/quickly-community-templates](https://launchpad.net/quickly-community-templates)

To install the templates:
    sudo add-apt-repository ppa:quickly-templates-hackers/quickly-community-templates-daily
    sudo apt-get update
    sudo apt-get install quickly-ubuntu-qt-template

To use the templates:
    HTML app: quickly create ubuntu-html-app
    Qt app: quickly create ubuntu-qt-application
    Qt Quick app: quickly create ubuntu-qtquick-application
    Unity lens: quickly create unity-lens

I'm using ubuntu-html-app template to use WebKit for HTML5 development rather than Python. But you might prefer to stay with Python throughout.  Your choice.

Here is a tutorial to help in your first app.

[https://www.youtube.com/watch?v=sO8hiPreNBg](https://www.youtube.com/watch?v=sO8hiPreNBg)

...

Now from your developed Ubuntu app you can use SSH tunnel to access your headless server to return and display your data in a required format. But that is polling rather than push.

...

But the above is only one idea and I'm sure you'll get other ideas along the way.

You could experiment with a headless server running as VM on VirtualBox in your development platform.

---

### Post by mrJTparadise on 2015-01-05
Great information dragonfly, this will come to use.

> [COLOR=#000000]Would you wish to have the headless server [/COLOR]_push_[COLOR=#000000] a stream of changing voltages, temperatures and other changing data ... to a community of users .. rather than have users [/COLOR]_poll_[COLOR=#000000] the headless server services via SSH tunnel?[/COLOR]

The information on this server is only being relayed to a single user and not a group of people.

Let me explain a scenario and maybe you can answer the question.

Suppose I am running Ubuntu 14.04 without the GUI desktop and is strictly command line.  The user will have two options - interact with the machine stricty by command line or have the option to interact with the machine with a custom made GUI - the GUI that I make.  [COLOR=#000000]To start up and run the GUI, I DO NOT want to have to enter the default graphical desktop UI and then start the custom GUI - I want the user to be able to type something as simple as gui in the command line and my custom make GUI will pop up. 

Is this possible or does Ubuntu need to be in desktop/graphical mode to display GUIs?  Would I be able to run xwindows or x11 in the background and then run the GUI in the foreground, keeping myself in my CLI interface?

If referring to the server/client model of things, both the server and client will live locally on the machine.  For example, the user would click a checkbox and when clicked, a box would display something in a box - just a very broad and simple example of an event.

Does what I am asking make sense?  I feel like we may have gotten confused with each other throughout these posts.

Thanks again dragonfly.

[/COLOR]

---

### Post by ian-weisser on 2015-01-05
It sounds to me like a use case for a GUI application on the user's device, but not the server.
The application communicates with the server, and translates the returned data into pretty.

You don't need a GUI on the server to do this.
To do this, you first define an API (exactly what can the client ask for, and exactly what will the server respond with).
Then you write a server application (non-GUI) that listens for a network connection, receives those API queries, and sends those API responses.
Then you write a text-only (non-GUI) client that converts user input into those API queries, and converts those API responses into useful output.
Then you write a GUI client that does the same thing as the command line client, but prettier.

---

### Post by mrJTparadise on 2015-01-05
The user's device is the actual Ubuntu 14.04 server though.

*Edit : What I am asking is pretty simple, can I start my GUI and interact with it from the command line WITHOUT having to boot into desktop mode (startx, x11, xorg, kde, etc.) ?*

---

### Post by Holger_Gehrke on 2015-01-05
> **mrJTparadise said:**
> The user's device is the actual Ubuntu 14.04 server though.

*Edit : What I am asking is pretty simple, can I start my GUI and interact with it from the command line WITHOUT having to boot into desktop mode (startx, x11, xorg, kde, etc.) ?*

Are you talking about writing a GUI on a machine without X ? Do you mean a text-mode pseudo GUI á la old DOS programs like Borland's Turbovision or a real Graphical User Interface ? If the first, have a look at curses. If it's the latter, than you'll have to look at directly working with the frame buffer device, like one usually does on embedded Linux systems ...

---

### Post by dragonfly41 on 2015-01-05
If you are reluctant to install xvfb here are some more ideas to throw into the pot ..

Use phantom.js to render the captured data on headless server

Use Raphael.js to create SVG image of voltage/temp readings.

Export as SVG or PDF or other format to be retrieved by user or sent to user.

...

[http://phantomjs.org/screen-capture.html](http://phantomjs.org/screen-capture.html)

which can be used with raphael.js 

[http://raphaeljs.com/](http://raphaeljs.com/)

to create voltage/temperature images in SVG

as here for example ...

[http://techoctave.com/c7/posts/17-jquery-dashboard-gauges-using-raphael-xhtml-and-css](http://techoctave.com/c7/posts/17-jquery-dashboard-gauges-using-raphael-xhtml-and-css)

or .. just here .. [http://raphaeljs.com/analytics.html](http://raphaeljs.com/analytics.html)

---

### Post by ian-weisser on 2015-01-05
> **mrJTparadise said:**
> The user's device is the actual Ubuntu 14.04 server though.

*Edit : What I am asking is pretty simple, can I start my GUI and interact with it from the command line WITHOUT having to boot into desktop mode (startx, x11, xorg, kde, etc.) ?*

Well, you can easily start/stop the GUI environment; you need not boot into it. Booting into GUI is controlled by the /etc/init/lightdm.conf Upstart job, and easily disabled. Once autostart is disabled, starting/stopping lightdm from the command line is also pretty easy. But I think that's not your question.

The only realistic 'yes' answer I see for a single application is to use ncurses (which is included in Ubuntu).
I don't think writing your own framebuffer and essentially your own X replacement is worthwhile. It would really be re-inventing the wheel (and the axle, and the driveshaft, and the muffler...)
Normal GUI applications rely on the high-level tools provided by GUI Desktop Environments, which rely in turn on the low-level tools provided by X. The entire stack must be running for a normal GUI application to work properly.

---

### Post by coldraven on 2015-01-06
Would Zenity work in this situation?

[https://help.gnome.org/users/zenity/stable/](https://help.gnome.org/users/zenity/stable/)

[http://en.wikipedia.org/wiki/Zenity](http://en.wikipedia.org/wiki/Zenity)

---

### Post by Holger_Gehrke on 2015-01-06
> **coldraven said:**
> Would Zenity work in this situation?


No, Zenity is just a tool to generate GTK/X11 dialogs from the shell. Without X and GTK and dbus all running, you get a couple of error messages but no dialogs.

---

### Post by ian-weisser on 2015-01-06
> **coldraven said:**
> Would Zenity work in this situation?

Last time I looked, Zenity relied upon GTK being present and operating...which needs X.

---

### Post by HermanAB on 2015-01-06
It sounds like you want to re-invent yet another SNMP system.  Do have a look at Nagios, OpenSNMP and Zabbix before you do that.

---

### Post by mrJTparadise on 2015-01-07
When sitting at the station I want the user to be able to pick either from the traditional command line or my custom made GUI that contains radio buttons, check boxes, etc. and that is it.  Judging by the answers it looks like this isn't possible?

---

### Post by Holger_Gehrke on 2015-01-07
Take a look at 'dialog'. It basically does the same thing as 'zenity' but in text-mode. Depending on what you're trying to do it might be what you need.

---

### Post by ian-weisser on 2015-01-07
> **mrJTparadise said:**
> When sitting at the station I want the user to be able to pick either from the traditional command line or my custom made GUI that contains radio buttons, check boxes, etc. and that is it.  Judging by the answers it looks like this isn't possible?

I think you have judged the answers accurately.

---

### Post by HermanAB on 2015-01-07
If you just want to monitor processes, then Netsnmp will do your command line actions and Zabbix the GUI.

---

### Post by dragonfly41 on 2015-01-07
I still think that one possible solution (which I posted earlier .. post #2) is for OP to install and use webmin and then setup usermin to grant user access to a restricted subset of features .. e.g. a script to monitor temperature and voltage (OP does not clarify what is the object being monitored).

So the admin would setup webmin via [https://ipaddress:10000](https://ipaddress:10000)
and the user (with subset of permissions) would access usermin via [https://ipaddress:5000](https://ipaddress:5000)


Here is a writeup on such usage ..


[http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html](http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html)


[http://www.havetheknowhow.com/Configure-the-server/Monitor-server-temperatures.html](http://www.havetheknowhow.com/Configure-the-server/Monitor-server-temperatures.html)


cron script

[http://www.havetheknowhow.com/scripts/CPUTempShutdown.txt](http://www.havetheknowhow.com/scripts/CPUTempShutdown.txt)


Instead of monitoring server temperature, other parameters can be monitored in similar way.

See webmin custom commands which can trigger a bash script to run instead of cron.

It may be that webmin is regarded as overkill but it is very easy to install.

---

