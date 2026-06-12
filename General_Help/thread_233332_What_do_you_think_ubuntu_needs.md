---
title: "What do you think ubuntu needs?"
date: 2006-08-09
forum: General Help
---

### Post by rekahsoft on 2006-08-09
I have been thinking lately about what Ubuntu could do to become better...i was reading around and started to look at AppleScript. For those of you who don't know what this is, it is a simple scripting language that lets you automate tetious processes. You can even make full blown programs with it!! You can have it use other applications to get the work done too...i think this is one of the most killer features ever and i would love to see it come to linux. Maybe an extension to shell would do the trick but i think it would need to be something entirly new with a very simple sintax like applescript so that basicly anybody can learn. Imigine being able to control any gtk2 application to automate things like making a blog, publishing a website, or getting the newest wallpapers from your favourite site. Imagine the possablitys and the power :)

---

### Post by wieman01 on 2006-08-10
What I'd love to see is a sophisticated & all-round Wireless Network Management application similar to NetworkManager but with the enhancements that it obviously needs (i.e. hidden ESSID, static IP, password management).

Wireless solutions are still in its infancy under Linux & I'd like to see it improved soonest.

---

### Post by -deadcats on 2006-08-10
> **rekahsoft said:**
> I have been thinking lately about what Ubuntu could do to become better...i was reading around and started to look at AppleScript. For those of you who don't know what this is, it is a simple scripting language that lets you automate tetious processes. You can even make full blown programs with it!! You can have it use other applications to get the work done too...i think this is one of the most killer features ever and i would love to see it come to linux. Maybe an extension to shell would do the trick but i think it would need to be something entirly new with a very simple sintax like applescript so that basicly anybody can learn. Imigine being able to control any gtk2 application to automate things like making a blog, publishing a website, or getting the newest wallpapers from your favourite site. Imagine the possablitys and the power :)

I don't understand. How is this different from simple shell scripting?

regards,
-dc

---

### Post by rekahsoft on 2006-08-10
It is different because it lets you use other applications to get work done...on macbreak (the podcast) they show how to automate a cellphone blog...all you do is email the picture/s to your email and it automaticly adds them to your cell phone blog and then publishes it...can you do that with shell? This is only one of the many things you can do...to see more examples google it or look on apples website.

---

### Post by chaosgeisterchen on 2006-08-10
You can do almost everything with shell...

---

### Post by rekahsoft on 2006-08-10
Yes you can do almost everythign with shell but can u do an automated cell phone blog like i mentioned above? applescrip just does a better job of interacting with applications...if linux were to ever get a feature like this it would probably be a gtk extension that lets shell interact with gtk apps...it also could be built right into the gtk app...

---

### Post by kabus on 2006-08-10
This thread belongs in the Cafe.

---

### Post by chaosgeisterchen on 2006-08-10
Well.. I already saw bash scripts interacting with Qt-Apps.. it was sth about Amarok, but I dunnot know whether this also works for GTK-apps...

Well, all of them have backends, all of them can be run in command line as well, so - why not controlling them via command line.

---

### Post by Buffalo Soldier on 2006-08-10
> **rekahsoft said:**
> I have been thinking lately about what Ubuntu could do to become better...i was reading around and started to look at AppleScript. For those of you who don't know what this is, it is a simple scripting language that lets you automate tetious processes. You can even make full blown programs with it!! You can have it use other applications to get the work done too...i think this is one of the most killer features ever and i would love to see it come to linux. Maybe an extension to shell would do the trick but i think it would need to be something entirly new with a very simple sintax like applescript so that basicly anybody can learn. Imigine being able to control any gtk2 application to automate things like making a blog, publishing a website, or getting the newest wallpapers from your favourite site. Imagine the possablitys and the power :)

The choices are not perfect, but these are the options that we have so far:[list=a]
[*] bash:[list]
[*] [Bash by example, Part 1](http://www-128.ibm.com/developerworks/library/l-bash.html)
[*] [Bash by example, Part 2](http://www-128.ibm.com/developerworks/library/l-bash2.html)
[*] [Bash by example, Part 3](http://www-128.ibm.com/developerworks/library/l-bash3.html)
[*] [Script library](http://www.linuxcommand.org/script_library.php)[/list]

[*] [Shell wrappers](http://www.tldp.org/LDP/abs/html/wrapper.html)

[*] [Python Does Scripts and Objects](http://www.byte.com/art/9702/sec5/art4.htm)
> [i]"Python got its start through its powerful scripting features. It is often presented as a bridge between Unix shell programming and C programming..."

"Another of Python's strengths is that it is scalable. Python programs can be short shell scripts or simple function-based programs. They can also be full-blown object-oriented applications handling large jobs..."[/i]

[*] [IPython: An enhanced Interactive Python shell](http://ipython.scipy.org/)
> [i]"One of Python's most useful features is its interactive interpreter. This system allows very fast testing of ideas without the overhead of creating test files as is typical in most programming languages. However, the interpreter supplied with the standard Python distribution is somewhat limited for extended interactive use.

IPython is a free software project (released under the BSD license) which tries to:

1. Provide an interactive shell superior to Python's default. IPython has many features for object introspection, system shell access, and its own special command system for adding functionality when working interactively. It tries to be a very efficient environment both for Python code development and for exploration of problems using Python objects (in situations like data analysis).

2. Serve as an embeddable, ready to use interpreter for your own programs. IPython can be started with a single call from inside another program, providing access to the current namespace. This can be very useful both for debugging purposes and for situations where a blend of batch-processing and interactive exploration are needed.

3. Offer a flexible framework which can be used as the base environment for other systems with Python as the underlying language. Specifically scientific environments like Mathematica, IDL and Mathcad inspired its design, but similar ideas can be useful in many fields.

4. Allow interactive testing of threaded graphical toolkits. IPython has support for interactive, non-blocking control of GTK, Qt and WX applications via special threading flags. The normal Python shell can only do this for Tkinter applications."[/i]

[/list]

---

### Post by rekahsoft on 2006-08-10
In my opinion IPython looks the best for the job...how would this work with the gtk and other gnome apps?

---

