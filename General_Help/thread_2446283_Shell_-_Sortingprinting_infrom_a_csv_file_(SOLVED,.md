---
title: "Shell - Sorting/printing in/from a csv file (SOLVED, and changed topic!)"
date: 2020-06-27
forum: General Help
---

### Post by ryanelias on 2020-06-27
Hello ! I'm a computer science student in France and I'm learning the shell language on ubuntu. The year is already over, but I am making a little project : an "agenda" using a csv file.

I already wrote a few functions that work pretty well, but a single problem blocks me from advancing.

First, let me explain the organization of my csv file :** each line is divided like this** : title,level_of_importance(integer, lower is more important),category(integer),person,date,hour,duration,remark . 

**Example of line** : Mom's birthday,1,1,Mother,30/09/2020,15:30,3h,My mother is the best !

The function that doesn't work for me is the one that prints only the events of a certain category. Here is my code (translated) : 
```

show_category()
{
echo "Please enter the number corresponding to your category : 
0 : Various
1 : Birthday
2 : Scores
3 : Party "
read num_cat
IFS=,
while IFS= read -r ln  
    do
        if [ "$3" = "$num_cat" ]
        then
            printf '%s\n' "$ln"
        fi
    done <"$file" | sort -t, -k2,2n | sort -t, -k3,3n  | show  # $file is my csv file , show is a function that prints on screen the content of a line in the file.
}
```

When I run that function, it does not do anything ! I tried replacing the "=" by a "-eq" but it returns me an error message " [: Illegal number: , so I abandoned this idea.

My objective is to print only the events of the entered category, using the function show (that works with other functions). 

Can you please help me understanding the reason why it doesn't work ? If needed, I can provide the function show, but it would add 27 lines to the message, which is already long enough in my opinion ! 

Thank you by advance !

---

### Post by Holger_Gehrke on 2020-06-27
How about just putting some output into the loop for debugging ? Just put 'echo $ln X $num_cat X $3 X' on a new line between 'do' and 'if' (the Xs are there to separate the variables visually, especially if one of them is unset or has an empty value ...). After that get ready to reread 'man bash' and pay attention to the rules on Word Splitting and the way the Builtin 'read' works.

Holger

---

### Post by ryanelias on 2020-06-27
Thank you for your answer. 
I added the line you provided me with, and it does print (literally) the lines of the csv file, each of them being followed by the (empty) printing format of my "show" function. It gave : 

~$ ./main.sh
[COLOR=#000000]Mom's birthday 1 1 Mother 30/09/2020 15:30 3h My mother is the best ! X 2 X X 

[/COLOR]        Importance : 
            Category : 
        The :  
            At :  min 
            Duration : 
    Remark : 
    *********************************************** 
~$ 
[COLOR=#000000]
About the word splitting, I set the IFS to ',' (and saved the original value), but I am a newbie and I still have a lot of things to learn, so I'll follow your advice and read the manual again. 

[/COLOR]

---

### Post by Holger_Gehrke on 2020-06-28
What the output of the echo shows: the complete line **without the commas**, the selected category and **nothing** for $3. Which is what I expected, since 'read' splits the line into words on IFS and assigns the words to the name**s**. If there's less names than words, the last name gets everything added to it for which there is no separate name. So $ln ends up having the complete line without the IFS. And nothing sets $3 (unless the function is called with three or more parameters).

You need to have one variable per field, change the condition to use the variable into which you read the categorie and change the printf to print all the variables separated by IFS for further processing.

Holger

---

### Post by &amp;wP*!) on 2020-07-01
A valid question from my side why a computer science student like you is not using languages like Perl or Python which have more advanced regular expression and data structure capabilities to process such things easier...

---

### Post by ryanelias on 2020-07-01
@pencuse Hello ! I am already learning Python, but we studied Shell this year, and not trying to learn a bit more about it would be a crime in my opinion.
I would like to thank both of you and @Holger_Gehrke for your advices ! 
Sincerely yours,
ryanelias.

---

### Post by dragonfly41 on 2020-07-01
Late note. Perhaps extend your studies to take in.. [HaXe]("https://haxe.org/manual/introduction-haxe-history.html") .. which transpiles common code base to Python, PHP, Javascript, Node, Java, Lua, CLI...

"The Haxe project was started on 22 October 2005 by French developer Nicolas Cannasse ..."

[HaXe]("https://haxe.org/manual/std-regex.html")[ ]("https://haxe.org/manual/std-regex.html")[regex]("https://haxe.org/manual/std-regex.html")

---

### Post by TheFu on 2020-07-01
A few suggestions from an old-guy:
[LIST]
[*]Don't use a , as the separator; use something like the '|' instead. Nobody uses a | in their text but ',' is used all-the-time.
[*]I’d implement this solution using getopts() and **egrep** with a case/switch instead.  Menus are to be avoided in shell scripts.
[*]Look at todo.sh for examples of most what you probably want. google will find it.
[/LIST]

A few times a month, I’ll implement a script that uses bash getopts() and makes calls to egrep  and awk. As soon as the script is over 1 page long, I’ll switch to a better language like perl which has great support for data structures unlike bash.  The right tool for the right job.

Don't reinvent the wheel when well-tested, proven solutions exist.  if you want a menu, jump to zenity [https://help.gnome.org/users/zenity/](https://help.gnome.org/users/zenity/) or some TUI library implementation like dialog+ncurses-cli.  [https://invisible-island.net/dialog/](https://invisible-island.net/dialog/)  Life is too short to have crappy ui.  Plus, you can implement a batch mode easier.

---

### Post by ryanelias on 2020-07-01
@dragonfly41 Good morning ! I read the page about HaXe , it looks quite interesting ! I will surely talk about it to some of my teachers ! The thing I don't get is the way the code is "converted" into other languages (I'm far - far away from being an experimented developer !). The only sure thing is that I will at least read the documentation about it, by curiosity.

@TheFu Thank you for the advices ! I will read some documentation about the solution you told me about (using getopts() and egrep).  

The multiple opinions I got in the replies to this publication encourage me to learn different skills, but would it be wise to study multiple languages in the same time ? I would not like to be called Jack of all trades, master of none !

Thanks by advance !

---

### Post by TheFu on 2020-07-01
> **ryanelias said:**
>  The multiple opinions I got in the replies to this publication encourage me to learn different skills, but would it be wise to study multiple languages in the same time ? I would not like to be called Jack of all trades, master of none !

There's little reason to master bash.  We only need enough to handle short, 1pg or less, scripts.  Anything longer is expected to use another language for maintainability reasons.  Bash data structures are ugly to use and there is little reason to bother. We have python, ruby, perl, when non-trivial scripts are needed.

1 more suggestion - use a yyyy-mm-dd date instead.  date "+%F" outputs this and it sorts much smarter.

if you have 6 months of python, that should be sufficient to do multiple languages. Your brain compartmentalizes them just like it does with different spoken languages.  

Being an expert in bash really won't get you paid more, but being an expert in python or perl definitely will.

---

### Post by ryanelias on 2020-07-08
Well, it looks like I will have to focus on Python ! I would like to thank all of you for your advices !

---

