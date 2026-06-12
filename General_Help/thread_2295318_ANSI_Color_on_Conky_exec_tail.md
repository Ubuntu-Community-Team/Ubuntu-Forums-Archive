---
title: "ANSI Color on Conky exec tail"
date: 2015-09-17
forum: General Help
---

### Post by jcllings on 2015-09-17
So I'm tailing logs and I want any occurrences of the word "ERROR" or "Exception" to be red.  How can I get this?

Jim C.

---

### Post by QDR06VV9 on 2015-09-17
You would need to add a Color scheme Like this 
```
# Color scheme #
default_color FFFFFF (Which would be white)


color1 FFFFFF
color2 C10E24 (This is a Red Color)
color3 ?????
```


To get the color you prefer I would use a tool.
I recommend GPick:

```
sudo apt-get install gpick
```

Applications -> Graphics -> GPick


It's got a lot more features than gcolor2 but is still extremely simple to use - click on one of the hex swatches, move your mouse around the screen over the colours you want to pick, then press the space bar to add to your swatch list.


It also has a traditional colour picker (like gcolor2) in the bottom right-hand corner of the window to allow you to pick individual colours with magnification.
Now this is for Conky if I understand you.
Regards

---

### Post by CantankRus on 2015-09-18
Use sed to replace "ERROR" with "${color red}ERROR${color}" and execpi to parse conky variables.
From man conky...
>  **execp** command
[INDENT]Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. 
I'd recommend coding wanted behaviour in C and posting a patch. This differs from $exec in that it parses the output of the command, 
so you can insert things like ${color red}hi!${color} in your script and have it correctly parsed by Conky. 
Caveats: Conky parses and evaluates the output of $execp every time Conky loops, and then destroys all the objects. 
If you try to use anything like $execi within an $execp statement, it will functionally run at the same interval that the $execp statement runs, 
as it is created and destroyed at every interval.[/INDENT]

 **execpi** interval command
[INDENT]Same as execp but with specific interval. Interval can't be less than update_interval in configuration. 
Note that the output from the $execpi command is still parsed and evaluated at every interval.[/INDENT]

eg using different colors for "ERROR" and "Exception"....
```
${execpi 1800 sed -e 's/ERROR/${color red}ERROR${color}/g' -e 's/Exception/${color yellow}Exception${color}/g' ~/log.txt}
```

You may need to increase the default values of these settings in your conky config above "TEXT"...
```
text_buffer_size 2048
max_specials 2048
```
 

In addition to runrickus's suggestions, zenity which is installed by default has a color picker.
```
zenity --color-selection
```
You can create a bash alias for ease of use (add to ~/.bash_aliases)...
```
alias zcolor='zenity --color-selection'
```

---

