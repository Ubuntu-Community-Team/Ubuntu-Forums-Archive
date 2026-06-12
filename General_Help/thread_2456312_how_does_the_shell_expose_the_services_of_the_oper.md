---
title: "how does the shell expose the services of the operating system to another program?"
date: 2021-01-09
forum: General Help
---

### Post by thehappybilly on 2021-01-09
so i am doing research into what a shell is and i found this wikipedia article [https://en.wikipedia.org/wiki/Shell_(computing)](https://en.wikipedia.org/wiki/Shell_(computing))






and it says "In computing, a shell is a computer program which exposes an operating system's services to a human user or other program."






my question is, "exposes an operating system's services to a human user or other program." what does the "other program" mean? i understand that it acts as an interface between the human user and the operating system, but i don't understand the "other programs" part

thanks

---

### Post by Impavidus on 2021-01-09
The other program could be a shell script.

---

### Post by Holger_Gehrke on 2021-01-09
There are three ways I understand this part of the explanation:
[LIST]
[*]Other programs can call the shell to do some of the things it is good at, like setting up pipes for processing jobs made up of distinct steps (example: write out some data as text then call "bash -c 'sort < the_file_i_just_wrote | uniq > sorted_file_with_duplicates_removed' "). This isn't necessarily limited to shell scripts, you can do this from any programming language that allows you to call other programs. 
[*]Also the shell will do some things to the command line like substituting variable values for their names, transforming globs (expressions involving "wild card"-characters) into lists of files or command substitution (inserting the output of one program into a call to another programm). This can be seen as a service the shell performs for these programs; almost none of the usual command line programs can handle wild cards, they all rely on the shell to do this for them before they are even started ... 
[*]And of course the shell also handles input and output redirection, so a program doesn't even need to have the concept of a file; it just reads from standard input and writes to standard output and the shell sets these up before the program is started. There's a whole class of programs - usually called filters - which work this way. 
[/LIST]

Holger

---

