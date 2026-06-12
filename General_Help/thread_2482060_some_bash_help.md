---
title: "some bash help"
date: 2022-12-18
forum: General Help
---

### Post by strange on 2022-12-18
i want to run a python script from within a bash script ie 
python3 /location/of/script.py $1

and then get the output from that script and use it further down the bash script
the output for the python script is :

[INFO] 18/12/2022 07:36:46 AM - Getting details for ID_12
[INFO] 18/12/2022 07:36:47 AM - URL Link : [https://this.is.what.i.need.to.get.url](https://this.is.what.i.need.to.get.url)
[INFO] 18/12/2022 07:36:47 AM - Parsing URL to get SOMETHING
[INFO] 18/12/2022 07:36:48 AM - No cached data found
[INFO] 18/12/2022 07:36:51 AM - Found STUFF


--stuff thisineedtoo
--stuff thisineedaswell
--stuff alsothisineed

[INFO] 18/12/2022 07:36:51 AM - Inserting stuff to database
[INFO] 18/12/2022 07:36:51 AM - Inserted successfully

i would like to get whatever comes after " - URL Link :" to be $link
and i would like to write however many --stuff outputs there to a stuff.txt file that only contains the outputs not the "--stuff" can someone tell me how this is done?

---

### Post by matthewrkarlsen on 2022-12-18
Hello strange,

I don't write shell script very often, but the script below should work.
I'm sure someone else will be able to supply a more efficient version.

```

# edit: removed; apparently non-functional; etc

```

Edit: Caveat: [I]Ideally this script should be read through and understood before it is run.
 One could assemble the script in increments to understand each separate part in turn.[/I]

Regards,
Matthew

---

### Post by strange on 2022-12-18
it doesnt seem to work...
when i read the script i dont understand how $link gets defined you echo it but i dont see it etting defined higher up or am i misreading it?

---

### Post by strange on 2022-12-18
nevermind result= link= does it but yeah it doesnt seem to work

---

### Post by matthewrkarlsen on 2022-12-18
Hello strange,

Sorry to hear that it's not working as hoped.

May I ask: did you put the full code in a file, such as **[COLOR=#000000][FONT=courier new]script_name.sh[/FONT][/COLOR]** and then run using **[FONT=courier new]bash script_name.sh[/FONT]**[FONT=arial] or are you running it in some other way?

The first line of the script runs the python script and assigns the resulting output to RESULT (accessed via $RESULT).
The second line then extracts the LINK (accessed via $LINK) using the contents of RESULT.
The remaining lines create the file, again using RESULT.

When you run the script, what output do you see on the console?
Also, what is the contents of the stuff.txt file once run?

How exactly does the python script output the log details? Is it just using print("line here") for example, or something more complex?

There may be small tweaks required. I have taken the python output to stdout be exactly as supplied above without variation...
 However, for instance, 'URL Link : ' might need the last space to be removed... it all depends on how predictable the output of the python script is.
I haven't supplied any input to the python script in the script provided above so you might need to customise it a bit.

When I run it I see the console output:
```

Extracted URL: https://this.is.what.i.need.to.get.url

```
and the file contents is
```

thisineedtoo
thisineedaswell
alsothisineed

```

Regards,
--Matthew
[/FONT]

---

### Post by MAFoElffen on 2022-12-18
I do some bash and python scripting... But I have a hard time 'guessing' exactly what your goal is without seeing some of your present code... or your logic flow...

For instance, when I get an idea of what I what to do, I template out my code first with comments on the goals, then logic flow of how to get there... Then the code to achieve that.

From what you have said so far, it could be hundreds of things, and we are only guessing what that might be.

Does that make sense?

---

### Post by TheFu on 2022-12-18
```
#!/bin/bash

RESULTS=$(python3 /location/of/script.py $1 )

echo $RESULTS

```

Seems simple enough, though I'd never trust the PATH and would specify the exact location of the python3 interpreter for safety.
I don't know if this gets just stdout or both stdout and stderr output. A test would make that clear quickly.

---

### Post by MAFoElffen on 2022-12-19
Or... If I mix trading off info from one to another and I want to pass more than one thing, I'll write to a temporary file with one script, and read it from another script to parse the dataset. 

There are many ways. For example exporting ENV variables.

---

### Post by TheFu on 2022-12-19
IPC has many methods - IPC - interprocess communication.  I have an entire book just on that method of programming.  I've shown the easiest method above. It is extremely common.  If you look at  MAFoElffen's system-info script, you'll see it a bunch.

For all the most common scripting things, the ABSG is amazing.  Highly recommended.  Google for "ABSG bash" to find it. Don't be afraid of the name. It covers all the simple stuff too.  There is a Beginners version, but I've never used it.  I already knew about 10 computing languages before I touched Unix, so while I was clueless about Unix, I wasn't clueless about programming.

---

