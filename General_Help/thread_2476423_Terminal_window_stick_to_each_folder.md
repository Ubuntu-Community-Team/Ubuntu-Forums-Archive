---
title: "Terminal window stick to each folder"
date: 2022-06-25
forum: General Help
---

### Post by bmebuntu on 2022-06-25
I would to question - suggest a new feature which is sticking the terminal window when you open inside a folder  to that folder so you can run script directly,
it can be added as option (similar to "show hidden files", it can be "show terminal")
This feature will become very handy if you are working with many folders and terminals that sometimes require checking one by one it become mess when you get many ones opened at the same time and you need to keep track of the instruction you make inside the folder
Perhaps setting a history of instruction to the right of the terminal (being similar to VS Code terminal)

---

### Post by Impavidus on 2022-06-26
This isn't really the place where we can send suggestions to the developers. That mostly goes through the bug reports or separate project websites.

Let me get this straight. What you want is a way to tie terminal windows to windows of the file manager, so that when you raise/put focus on a file manager window showing a particular directory, the terminal window in the same directory is raised automatically. Or a way to embed a terminal window in the file manager window, which may be easier as it doesn't require cooperation between file manager, terminal, shell and window manager – only between file manager and shell. And when you change directory in one, the other changes directory too. I can see how this would be useful to some people, those who use both the file manager and the terminal.

If you want to send feature requests to the people developing the file manager, best to explain precisely what you want.

---

### Post by Holger_Gehrke on 2022-06-26
There's a few problem's with your suggestion:

[LIST]
[*]This is a support forum by users for users. Almost no developers read this forum. You'd be better off posting this as a feature suggestion on the page/support area/... of the file manager you're using. 
[*]You misunderstand the way the terminal works. The terminal just gives text based input / output for programs that can't do graphical output and can't handle event-oriented input (programs that work like that are much easier to write ....). The actual command processing is done by the shell (usually bash, but there's way more than one shell ...). The commands executed are usually separate programs, too. 
[*]There's more than one terminal. 
[*]There's more than one file manager. 
[/LIST]

Something like the feature you want already exists in Krusader - a two panel file manager for KDE (the desktop environment Kubuntu is based on) - which has a terminal integrated at the bottom. Or you could use Midnight Commander, which is a two panel file manager that runs in the terminal and has a command line at the bottom.

A permanently visible history would be a waste of space IMHO. Most shells already have a history feature. In bash the command 'history' will give you a list of all commands prefixed with a number. Entering '!' directly followed by the number will re-execute that command. Or you can use 'ctlr-r' which does an incremental reverse search through history. Read the bash manual page (man bash) and search for 'history' (search in 'man' is started with the key '/'), but be warned: this gets very technical, very detailed and extremely dense.

Holger

---

### Post by TheFu on 2022-06-26
Use i3 as your window manager and learn to use the shortcuts.  It is painful, but once you have it down, you'll likely love it.

I use fvwm as my window manager and have 15 terminal windows start and get placed in very exact locations, including on different workspaces, to aid my efficient use.  One command starts the specific layout I want for coding, web development, video editing or a few other common tasks.  Use a GUI when it makes since, but don't confuse a GUI with efficiency. They align, perhaps 20% of the time where a GUI is the most efficient way to do something. The other 80%, a terminal and a few tiny scripts are 1000x faster.

I've never used an IDE on Unix. Never seemed needed and just got in the way of having 4 properly placed terminals where editing, compiling, debugging and function lookups were used in their specific terminal window.  I've been working like this for 25 yrs.  [https://blog.sanctum.geek.nz/series/unix-as-ide/](https://blog.sanctum.geek.nz/series/unix-as-ide/)  

I've been forced to use MSFT, Borland, and other coding tools on inferior OSes, but always miss the simplicity and efficiency of an Xterm on Unix for pure programming productivity.  The native Unix method of coding has been optimized since before the mid-1990s. They nailed it in amazing ways that bloated IDE users are missing. I weep just a little.

---

### Post by bmebuntu on 2022-06-26
Thank you guys for the useful advices. Trying new file managers i3 and Krusader  what I was thinking about is allowing file manage have docks  (similar to the QT GUI apps or Spyder) where you can tie as specific windows to the file manager or get it released as a separate window. The benefit of that is keep them contained together. The case of sticking the terminal to the file manager. is the most general use case. Suppose for example you want to experiment applying different scripts that transform images or files inside the folder (without using and programming ID) as you can use in machine learning projects. Then you stick the terminal you use it to run the script to the file manager you use to view the outcome of this script. When you do the same thing for many scripts and folders in parallel then such feature can be useful and efficient. I understand that generalizing this concept can be more challenging than it sounds, like in having one widget that allows the user to tie different apps (terminal, file manager, text editors ..etc)  and group them together in one block that you can show, hide, minimize or move together. The challenge may come from the constraints of each app itself (how to control the app by external processes or how it will respond and behave on events like minimizing or maximizing or closing ..etc). Though the simple utilities that are shipped with ubuntu (like text editor, office,  web browser, or terminal or file manager or timer) are likely to be much easier to start with. maybe such feature  can be set new standards for GUI application (including interopertability and exchanging information with other processes of the same group) to be responsive for docking and external processes control.
Your point is valid that special file managers or even IDE can be used, though the concept of grouping and docking apps together provide much flexibility, simplicity and efficiency in using resources or apply changes and it generalize better for general use case and combinations of the  selected apps.  For example, as you don't need all the features that comes with an programming ID (like VS code or Spyder) for something simpler like running scripts and definitely those IDE will not scale properly when you running different instants in parallel (as they will use more unnecessary and unused resources).


You are right, I suggest this feature to development. 
Thank you  for recommendations

---

### Post by Impavidus on 2022-06-27
> **bmebuntu said:**
> having one widget that allows the user to tie different apps (terminal, file manager, text editors ..etc)  and group them together in one block that you can show, hide, minimize or move together.The things you want to show, hide, minimise or move together are windows, not applications. Those are completely different things. Each window belongs to one application, but an application can have zero, one or more windows.
> The challenge may come from the constraints of each app itself (how to control the app by external processes or how it will respond and behave on events like minimizing or maximizing or closing ..etc).Nothing new here; every GUI application already has to deal with the window manager moving, minimising, resizing or closing the window. Applications may ask the window manager to forbid some of these actions, but there's no guarantee the window manager will honour that request.
> maybe such feature  can be set new standards for GUI application (including interopertability and exchanging information with other processes of the same group) to be responsive for docking and external processes control.There are already standard ways of interprocess communication: pipes, sockets and temporary files. The new thing you want is to tell processes to which group they belong, so they can find other processes belonging to the same group. This could be done via environment variables, which can for other processes be looked up in /proc (but are fixed after the process has started). But again, process &#8800; window. Note that there already is a concept of a [process group]("https://en.wikipedia.org/wiki/Process_group"), but that's probably not what you want.

So, you want a window manager feature. There are many window managers around and maybe one of them already has this feature. If not, pick a window manager you like and ask the devs to add this feature. Or join the devs and add it yourself, if they agree it could be useful.

When I use multiple windows to work on the same project, and another set of windows to work on something else, I put the windows belonging to the same project on the same or adjacent workspaces. I've got 15 workspaces in a 3×5 grid, which is usually enough. Putting everything together on one workspace and using minimise/restore looks like the hard way.

---

### Post by dragonfly41 on 2022-06-27
Since Krusader has been referred to in post#5, this is one file manager (GUI) that offers:

- embedded terminal panel (synced to the selected folder/file in dual panel)
- useractions which build actions using variables such as absolute file path, absolute folder path etc. etc.

Create a custom UserAction to see the variables.

I use Krusader UserActions to launch tool chains.

Examples:
Krusader to VSCode
Krusader to PHP server
Krusader to Pandoc
Meld
...

I use Krusader as my orchestrator. My "Houston command centre"

I'm sure that "clustering" of processes can be orchestrated quite easily.

I also use Krusader in company with automation tools such as Albert, xdotools, Actiona.

Added note: Krusader can also assign to different virtual workplaces as discussed in previous post.

---

### Post by bmebuntu on 2022-06-28
> **Impavidus said:**
> The things you want to show, hide, minimise or move together are windows, not applications. Those are completely different things. Each window belongs to one application, but an application can have zero, one or more windows.
Nothing new here; every GUI application already has to deal with the window manager moving, minimising, resizing or closing the window. Applications may ask the window manager to forbid some of these actions, but there's no guarantee the window manager will honour that request.
There are already standard ways of interprocess communication: pipes, sockets and temporary files. The new thing you want is to tell processes to which group they belong, so they can find other processes belonging to the same group. This could be done via environment variables, which can for other processes be looked up in /proc (but are fixed after the process has started). But again, process &#8800; window. Note that there already is a concept of a [process group]("https://en.wikipedia.org/wiki/Process_group"), but that's probably not what you want.

So, you want a window manager feature. There are many window managers around and maybe one of them already has this feature. If not, pick a window manager you like and ask the devs to add this feature. Or join the devs and add it yourself, if they agree it could be useful.

When I use multiple windows to work on the same project, and another set of windows to work on something else, I put the windows belonging to the same project on the same or adjacent workspaces. I've got 15 workspaces in a 3×5 grid, which is usually enough. Putting everything together on one workspace and using minimise/restore looks like the hard way.

Similar to window manager but a standardized socket communication between apps. Since each app is developed in different way setting such standard across different app to interact with external process can be useful in the long run. So I don't think that it is going to be a "single feature" for a window manager. But it is just a standard ways in programming apps to be compatible with an external application that manage the manage the communication between them and control their appearance and behavior as if they were a one application (despite of having different processes to run on each) with some caveats about synchronized performance.  Without such feature or development, it is very unlikely for app developer to think of any valid use cases that allow having control over the app by external processes ( say to justify implementing socket or to build an API to respond to external operations) some apps do have that but most of them do not. Whereas developing such application on grouping app together can allow implementing such standard interoperability across different application in compatible ways. that can have some useful use-cases.      

When I said "application" I mean "GUI application" and I used application it will be unpractical for such feature to be developed on "windows" level like when you have an application with multiple graphical interfaces, then to make control over one of these interferce (or windows) as it may not be practical to standardize getting the handler of window controlled by external processes when you develop a feature that to different applications.

---

### Post by Holger_Gehrke on 2022-06-28
That "standardized socket communication between apps" already exist. It's called 'dbus'. Any program - and it doesn't have to be a GUI application - can ask for a name on the bus, offer interfaces for controlling it and listen to messages. An example of an application that uses this is the pulse-audio panel app in XFCE which allows you to control all media players on your system which follow MPRIS (Media Player Remote Interfacing Specification). This includes starting a player, starting or pausing playback and skipping back and forth in the playlist. So the low level infrastructure is in place.

Holger

---

