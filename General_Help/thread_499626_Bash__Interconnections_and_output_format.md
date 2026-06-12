---
title: "Bash : Interconnections and output format"
date: 2007-07-12
forum: General Help
---

### Post by tacubuntuforums on 2007-07-12
Hi!

I was having trouble using the command *head* in Linux bash when I realized that using *head* and *grep* (and probably many other too) as interconnections after a command, not only displays filtered output lines but it actually changes their format.
I don't think this is a bug as it is something that everybody must come across someday but I don't understand why does it work like that.

To make it simple, take, as an example, these 3 instructions:
[I][B]1) aptitude search java 
2) aptitude search java | head -25
3) aptitude search java | grep concurrent[/B][/I]

The output of instruction 1) is different from that of 2) and 3) even on the corresponding lines, which I understand that, in theory, they should be exactly the same. The output is different because the columns are distributed differently. Hence a column may be cut when using an interconnection to filter some lines. Moreover, if I combine the output with the command ***cut***, to extract that column, I may get contradictory (different) results.

I would like to understand:
a) why does this happen (meaning at which point, the 'mechanism')
b) If it is done on purpose, for what reason
c) How to overcome these anomaly

Also:
I'd like to know if there's a command that filters and displays not only the head or tail of a file or standard input, as  *head* and *tail,*, but displays any interval of lines, that is, from line n to line m. Which, I think, would be more practical than having two commands and having to combine them to display any interval.

Thanks

---

### Post by stylishpants on 2007-07-12
> **tacubuntuforums said:**
> Hi!

I was having trouble using the command *head* in Linux bash when I realized that using *head* and *grep* (and probably many other too) as interconnections after a command, not only displays filtered output lines but it actually changes their format.
I don't think this is a bug as it is something that everybody must come across someday but I don't understand why does it work like that.

To make it simple, take, as an example, these 3 instructions:
[I][B]1) aptitude search java 
2) aptitude search java | head -25
3) aptitude search java | grep concurrent[/B][/I]

The output of instruction 1) is different from that of 2) and 3) even on the corresponding lines, which I understand that, in theory, they should be exactly the same. The output is different because the columns are distributed differently. Hence a column may be cut when using an interconnection to filter some lines. Moreover, if I combine the output with the command ***cut***, to extract that column, I may get contradictory (different) results.

I would like to understand:
a) why does this happen (meaning at which point, the 'mechanism')
b) If it is done on purpose, for what reason
c) How to overcome these anomaly

Many other unix programs do this as well, including "ls".   It's aptitude itself that will be responsible for it in this case.

When you're writing one of these programs that operates on the command line, you can call the function "isatty" (see 'man isatty' for more info) to determine whether your output is going to a terminal or not.  If the output isn't going to a terminal, then it could be going into a file or a pipe.

Anyway, if the output is going to a terminal, then your program can query the terminal to find out how wide it is in characters.  (The terminal keeps track of this -- in bash, try 'echo $COLUMNS', then resize your terminal window and do it again -- it will have automatically changed.)  This is useful for your program to know so that it can make use of the full available width for its output.  

If the output is not going to a terminal, then this query cannot be performed.  After all, how wide in characters is a file or a pipe?  Often there is no meaningful answer to that question.  In this case, most terminal-aware unix programs default to the old 80-character standard.  If you look at the output from your examples, I'm pretty sure you'll find that the output from the first one is as wide as your terminal, while the output from the last 2 will be exactly 80 chars wide. 

If you want to see this done so you can put it in your own programs, read the 'isatty' man page and then look at the source code for programs like 'ls' and search for 'isatty'.  Remember that you can see the source for most Ubuntu packages with the 'apt-get source' command.  For example, for ls, do this:

```
cd /tmp
apt-get source coreutils
cd coreutils-5.97/coreutils-5.97/src/
view ls.c +/isatty

```


> **tacubuntuforums said:**
> 
c) How to overcome these anomaly


Choose your numbers for 'cut -b' based on the 80 char width.  Redirect the output to a file and look at it in a text editor that can show you what column number the cursor is at (eg. vim, emacs) if you like.

Or, instead of taking the approach of specifying certain fixed bytes for display, use 'awk' and just specify columns by number.  awk is easier to use for that approach than cut is.  In this case you might want to use 'apt-cache' to do your search instead of aptitude, to avoid the optional columns that aptitude gives you.

```

# print the first column
apt-cache search java | awk '{print $1}'

# print columns 5 and 8, separated by a tab
ls -l | awk '{print $5 "\t" $8}'

```

There's plenty of other ways to approach this, too.  Which one is correct depends on what you're trying to do.
 



> **tacubuntuforums said:**
> 
Also:
I'd like to know if there's a command that filters and displays not only the head or tail of a file or standard input, as  *head* and *tail,*, but displays any interval of lines, that is, from line n to line m. Which, I think, would be more practical than having two commands and having to combine them to display any interval.

Thanks

To view an range of lines defined by line numbers, you can use sed:
```

# view from line 18 to line 43
sed -n '18,43p' ls.c

# it works well in a pipe too, of course
cat file | sed -n '18,43p' 

```

---

### Post by tacubuntuforums on 2007-07-14
Thank you for your answers.
Your explanation is clear and makes total sense. I downloaded the source (first time I do that) as you suggested and saw the lines of code that help explain why ls prints its output in a number of columns according to the display's number of columns ($COLUMNS) or in one single column if goes to a pipe like in * ls | head *.

But I still don't understand why if the output goes to an interconnection then the program should decide to cut the lines 80 chars long. Why not passing the entire lines until the end of the line (carriage return, or whatever) and  let the last program in the interconnections format the lines according to the output device and  the number of columns if its a display (using isatty).

Because if the lines are cut when written in a pipe (as for a filtering purpose), then I will still get the original columns (from instruction nr. 1) wrong, that is, cut even if I use awk or sed, as you suggest.

Anyway thanks for the idea of using awk and sed. I should study those powerful and flexible commands again, because I hardly remember anything so I almost never use them.

So I understand that since there's a loss of data when some programs write long lines into an interconnection, there will be no way to overcome the 'anomaly' or 'misbehavior' I was pointing out, which is the cutting of lines/columns when piping through line-filtering processes (like *head*, *grep* or *sed.*). [COLOR="Red"]Maybe I wasn't clear enough...I'd like to be able to filter lines first, and then extract a column without any loss of data, which sounds to me like a very a very normal and  habitual thing to do.[/COLOR]

Do you think there's no way around?

Now I remember a similar problem ..... There are some programs that display their output in columns (n the console) but often, the columns are not wide enough so that the data in also cut in some lines, and you can't see  the whole information. That happens sometimes,  for example, when using *netstat*:

netstat -lp
netstat -tlp

And I haven't been able to overcome that either

---

### Post by stylishpants on 2007-07-15
This behaviour generally doesn't stop you from doing anything that you could otherwise do.  It isn't generally seen as a problem.

Maybe if you post some specific examples of things you're struggling with, we could help you address them specifically.  There's plenty of shell mavens lurking in this forum that love tackling this kind of thing.

---

### Post by Mr. C. on 2007-07-15
It would be safe to say that programs modifying their STDOUT/STDERR based upon TTY columns/rows is fairly rare, and has never presented a problem in all the years I've been working on Unix/Linux systems (and that's a lot of years).

As stylishpants asks, what specific problem are you seeing that you need a solution for ?

MrC

btw. we simply call them pipes - not interconnections.

---

### Post by tacubuntuforums on 2007-07-16
Since what I want to do seems something very common, and even I do it often, I think there must be a way to avoid the problem I'm talking about.

I said it very clear at the end:

>   ... which is the cutting of lines/columns when piping through line-filtering processes (like head, grep or sed.). Maybe I wasn't clear enough...[COLOR="Red"]I'd like to be able to filter lines first, and then extract a column without any loss of data, which sounds to me like a very a very normal and habitual thing to do.[/COLOR]

Do you think there's no work around?

the problem is the same I pointed at the very beginning. You just gave me an explanation why that happens. Ok, that's part of my original query, I appreciate your answer which helps me understand what's going on,  but it still happens. And if I use *sed *instead of *head* or *awk* intead of *cut* it still happens.

In the following instructions only the first one prints the whole information (if the display is wide enough). The other ones print only 80 chars per line so there's loss of information in some of the filtered lines. 

1) aptitude search java
2) aptitude search java | head -25
3) aptitude search java | grep concurrent
4) aptitude search java |  sed -n '18,43p'

So,

5)  aptitude search java |  sed -n '1,25p' |  awk '{print $2}' 

[COLOR="Red"]doesn't give me the piece of column as I see it in the output of 1)[/COLOR]

Therefore if one filters some lines and then cuts one column, he will get a different result than what "in theory" he expects or, at least, wants. 
When I filter lines, I just want to filter lines; I don't want those lines to be cut 80 chars long because I'm not going to obtain what I want.

[COLOR="Red"]So I'm almost sure that, since this seems to be a very usual thing to do, there must be a way to extract a column from a set of filtered lines without having loss of information[/COLOR]. But saying that there must be a way to do it, because it has been like that for years doesn't show me how to do it.

Later I also said:

> Now I remember a similar problem ..... There are some programs that display their output in columns (n the console) but often, the columns are not wide enough so that the data in also cut in some lines, and you can't see the whole information. That happens sometimes, for example, when using netstat:

netstat -lp
netstat -tlp

And I haven't been able to overcome that either

[COLOR="Red"]If it has been like that for years, then what is that people do when they want to see the whole information when the columns are too narrow and cut the lines.[/COLOR]

It seems that you are not understanding me, but how can I say it clearer....in general terms, often, when using the console the information is displayed in columns and often the columns are not wide enough to display the information without being cut. Since this may be caused in each case for different reasons and may have a different walk around, I gave you those two concrete examples, so that we can delimit the problem and find a concrete solution.

---

### Post by Mr. C. on 2007-07-16
Tacubuntuforums,

You are confusing some basic Unix/Linux concepts, and grossly exaggerating the problem space.

The pipeline and filter programs themselves are not affecting the original program.  They simply consume and produce STDOUT and STDIN respectively.  This is the way it works, and has worked very well for 30 years.

A program may produce any output it desires, in any format it desires. There is nothing that mandates or suggests that all programs should produce output in exactly the same way.  Programs that format their output specifically for *the screen* must make some compromises (wrap or cut).  Aptitude is one such program.  The ls program is another.

Aptitide has a --width option that can be used to control the width of the output field.  The ls command has the -1 option to produce single-columned output.

The tools are there to do what you want reliably - you just have to learn to use them correctly, and of course, read their man pages when seeking understanding and solutions.

I see no problem with netstat's output; it produces for me exactly the same output no matter where STDOUT is directed.  Perhaps you can show such output or examine it with od -bc.

Your general inferences and conclusions are based upon exaggerated and incorrect premises :

> Therefore if one filters some lines and then cuts one column, he will get a different result... 
...
often, when using the console the information is displayed in columns and often the columns are not wide enough to display the information without being cut


These conclusions, based upon an example or two, hardly suggest a rule.

When I asked you what real-life problem you were trying to solve, your response was not as clear as you seem to believe.  Instead of stating your *goal*, you gave command line *solutions*.  Instead of showing us exactly what output you were obtaining, you left it to the reader. In fact, your "concrete" examples seem to be fickle to you, but are supposed to be clear to me ("That happens *sometimes*, for example, when using netstat:").  Perhaps it works for me because this is some other time.

Had you asked "how do I get Aptitude's full text description?", you would have received a specific answer.  Its also more helpful if you show your command output so that other's can work from what you are seeing, and not frustrate themselves trying to replicate your "sometimes".

MrC

---

### Post by tacubuntuforums on 2007-07-16
Hello Mr C.:

I can hardly believe it. What are you telling me?
You are not saying anything I don't know. I am not confusing any Linux/Unix concept and I am not exaggerating anything. You are exaggerating what I say.

> "The pipeline and filter programs themselves are not affecting the original program. They simply consume and produce STDOUT and STDIN respectively. This is the way it works, and has worked very well for 30 years

The pipeline and filter programs themselves are not affecting the original program. They simply consume and produce STDOUT and STDIN respectively. This is the way it works, and has worked very well for 30 years.

A program may produce any output it desires, in any format it desires. There is nothing that mandates or suggests that all programs should produce output in exactly the same way. Programs that format their output specifically for *the screen* must make some compromises (wrap or cut). Aptitude is one such program. The ls program is another."

This is the thing I have known for longer time about Unix/Linux systems.

> The ls command has the -1 option to produce single-columned output.

This has absolutely nothing to do with my question, with my problem, with my example; only very indirectly and remotely.

> I see no problem with netstat's output; it produces for me exactly the same output no matter where STDOUT is directed. Perhaps you can show such output or examine it with od -bc. 

I never said that netstat's output changes depending on the standard output. I just said that **_sometimes_**, yes **_sometimes_**, **_not always_**, the information that should be displayed is longer than the column's with, so the data is cut. That depends on what is coming out, depends on the hosts, and ports you are having connections with. I'll try to produce a situation where the addresses are long enough and post the example if it helps. I just thought that a little bit of imagination and experience from your side would be sufficient.

> "Your general inferences and conclusions are based upon exaggerated and incorrect premises :"When I say therefore x,y, and z

that is only a conclusion based on the empirical fact:

> 5) aptitude search java | sed -n '1,25p' | awk '{print $2}'
doesn't give me the piece of column as I see it in the output of 1)

mentioned right there.There are no exaggerated nor incorrect premises here.


What may happen is that you are not understanding what I'm saying which is so simple as saying if I filter this output, then the information is cut: exactly as Mr stylishpants said. He just told me how to look exactly when and how that happens in the code. But it continues to happen even with *sed* or *awk,* of course. I will explain it later again because I think you still just don't understand what I'm saying.
It seems to me that when you think that I'm trying to mean that "something goes wrong in Linux bash" you just can't stand it and think how come this newbie can be right when this has been working for 30 years. [COLOR="Red"]But even if it were 100 years, I still don't have an answer as to how extract a column without having it cut.[/COLOR] It must be very simple and super Unix/Linux systems sure have a simple easy walk around to my problem. But you haven't pointed it out, because you are more concerned in scolding me than in understanding me.

I may not be an expert in Unix/Linux systems, but I am in logical reasoning and it is an elemental matter that one single example may be sufficient to draw a 'general' conclusion. *Kurt Gödel needed to construct only ONE single sentence as an example with no demonstration at all, to proof that the whole arithmetic theory is not complete, cannot be complete and consistent,  and that truthfulness is not the same as demonstrablility*. You just need to see a single man die to say that the statement "all human beings live for ever" is false.

So the problem here is not that. The problem is that all your replies don't tell me [COLOR="Red"]how can I extract the list of packages that I see[/COLOR] from the output of:

**aptitude search java**

in a "simple" way.

Of course that I can manage to do it in a complicated way. I have done it several times. But I'm not happy having to think a particular and solution for every different output each time I have the similar problem.

I didn't want to state the problem just like that because, in this case, the list of packages is sometimes the second column and sometimes the third (taking as delimiter a string of blanks) and that is a particular additional element I just didn't want to consider. So, even if this is not what I want to do, we can simplify the problem in EXACTLY this ways:

[COLOR="Red"]a) List the first 25 packages from the output of *aptitude search java*
b) List the first 25 descriptions from the output of *aptitude search java*[/COLOR]

I didn't exaggerate absolutely anything I just said that using head and using *sed* or using *awk* in the ways I explained was not the solution, because it is not, just for that reason. I just need one example, one incorrect line to say that is not the solution.

I also said that there must be a work around because it's an everyday common thing to do and, of course, even if I didn't mention it, because it has been like that for 30 years in the Linux/Unix shells which are extraordinarily good and so many people use them and do the things I want to do like extracting a column..

And finally, I didn't asked :
>  "...how do I get Aptitude's full text description?", you would have received a specific answer.

for the simple reason that I don't understand that question myself. And as far as I know, human beings don't ask questions to other people when thay don't even understand what is being said in the same question.

If you don't feel like answering, just don't do it, someone will answer.

---

### Post by stylishpants on 2007-07-16
Actually he already answered your question.  See above.

To clarify:
```
aptitude -w $COLUMNS search java | head
```

---

### Post by Mr. C. on 2007-07-16
I gave you the answer in my response.  If you choose not to read and discover it, that's ok by me.

I won't continue this battle of wits with an unarmed man.  

Good day.
MrC

---

### Post by tacubuntuforums on 2007-07-16
Hi to both of you.

Am I'm hallucinating, are you kidding or what?


> aptitude -w $COLUMNS search java | head

is  a completely wrong solution.

Imagine that you are in an exam. And the questions, _as mentioned before_ are:

[COLOR="Red"]> a) List the first 25 packages from the output of aptitude search java
b) List the first 25 descriptions from the output of aptitude search java[/COLOR]

When the question in the "exam" says [COLOR="Red"]"List the first 25 packages"[/COLOR] it means [COLOR="Red"]"display a list of that and only that"[/COLOR], that is, "in each line one package and nothing else", of course. If not I don't need anything I've said or you've said, not even the -w $COLUMNS part.

So, according to you, the first paragraph of this thread, where I wrote that

"2) aptitude search java | head -25"

doesn't give me what I want,  is then a solution to what I want, also????? Because there I can also see the first 25 packages.

I don't want to see them, I want to extract that column (so I can write to a file the list of packages, in a "simple way", that is with a few commonplace comands)


Now maybe you understand that what seems my exaggeration of the problem and confusion of concepts is only an exaggeration of explanations in order to avoid answers that are no solutions to my point. Because a lack of reading or understanding takes us exactly to the starting point.

Now, what I expect is that you will come up  telling me to use a pipe with awk, which is not a solution either, as I have explained so many times,  because it cuts the column of packages and some packages, yes only "some", the long names, are going to be CUT.

---

### Post by tacubuntuforums on 2007-07-16
Mr C,

You shouldn't start it neither with an unarmed man nor with an armed one, because War is never an answer and, in this case, is not an answer to my question

---

### Post by stylishpants on 2007-07-16
> **tacubuntuforums said:**
> Hi to both of you.

Am I'm hallucinating, are you kidding or what?




is  a completely wrong solution.


Wow, after 127 posts, this is my first time getting flamed on the Ubuntu forums!  Feels like I'm back on usenet again.  Thanks for the trip down memory lane, dude.


> **tacubuntuforums said:**
> Hi to both of you.

Imagine that you are in an exam. And the questions, as mentioned before are:



When the question in the "exam" says [COLOR="Red"]"List the first 25 packages"[/COLOR] it means [COLOR="Red"]"display a list of that and only that"[/COLOR], that is, "in each line one package and nothing else", of course. If not I don't need anything I've said or you've said, not even the -w $COLUMNS part.

So, according to you, the first paragraph of this thread, where I wrote that

"2) aptitude search java | head -25"

doesn't give me what I want,  is then a solution to what I want, also????? Because there I can also see the first 25 packages.

I don't want to see them, I want to extract that column (so I can write to a file the list of packages, in a "simple way", that is with a few commonplace comands)


Now maybe you understand that what seems my exaggeration of the problem and confusion of concepts is only an exaggeration of explanations in order to avoid answers that are no solutions to my point. Because a lack of reading or understanding takes us exactly to the starting point.

Now, what I expect is that you will come up  telling me to use a pipe with awk, which is not a solution either, as I have explained so many times,  because it cuts the column of packages and some packages, yes only "some", the long names, are going to be CUT.

Look, me and Mr. C have both told you already that awk doesn't do that -- aptitude formats its output at an 80 char width before it ever gets to awk.  We've also both posted to show you how to address that problem.   What you do with that output later on is up to you.  I've already shown you how to deal with the other parts of your problem.  Put it together.

Maybe next time you'd get farther by posting examples of what commands you use, what results you get and what results you want.

I'm done.

---

### Post by tacubuntuforums on 2007-07-16
Ok stylishpants,

I'm sorry, but when I wrote "am I hallucinating or are you kidding?" that's exactly what came to my mind because after so much explanation and talk about the columns and cuts, and data loss,  that answer just doesn't take all that, the core of the problem, into consideration. And  I still can't see why you don't understand me, I really don't know. Maybe you are reading too fast and don't get the whole picture of what I want. You don't seem to use all what I have said to understand me, just little parts as if they were the whole message.

At the beginning I didn't want to give a very concrete formulation of the problem because the question is more general:

In many occasions the output of commands are displayed in columns and often I want to extract one of those columns or some of the lines in it (in the column), _without having any loss of information_, that is,  without getting a column narrower than when displayed in the original command. (I think this would be, what MrC calls "my goal").

Since my problem appears in different occasions I didn't want to express it in a very concrete way _only_, because I feared you will come up with a solution that  I could only apply to that case.

Now You tell me:
> Maybe next time you'd get farther by posting examples of what commands you use...

 I chose the "*aptitude search java*" example and told you what commands I use.I usually use ***head*** or ***grep,*** sometimes ***sed*** (in very simple ways) to filter lines (or substitute chains) and ***cut*** to extract columns.

What else do you want me to say? I use nothing else and I gave you the examples where is not working in the first post, instructions 1),2) and 3).
With the -w option, Mr C posted a way in which after applying the filters used in  2) and 3) we will obtain the complete lines of the original command, but still I can't extract the column which is the problem I've mentioned.

I didn't post any output because the specification of the problem is quite simple, I never thought it could be needed. Besides, your first answer to my initial post made me assume that you understood my problem perfectly well.

Then Mr C, not losing an opportunity to lecture me in every paragraph,  asked me to be more explicit and to give a concrete example:

> "When I asked you what real-life problem you were trying to solve, your response was not as clear as you seem to believe. Instead of stating your *goal*, you gave command line *solutions*. Instead of showing us exactly what output you were obtaining, you left it to the reader. In fact, your "concrete" examples seem to be fickle to you, but are supposed to be clear to me ("That happens sometimes, for example, when using netstat:"). Perhaps it works for me because this is some other time"

So I asked in the most explicit and concrete way I can:

> [COLOR="Red"]Imagine that you are in an exam (a situation where questions are concrete _and also answers need to be completely concrete and correct too_ )

a) List the first 25 packages from the output of aptitude search java
b) List the first 25 descriptions from the output of aptitude search java

"List the first 25 packages"  means "display a list of that and only that", that is, "in each line one package and nothing else"[/COLOR]

Just that. Let's start with that. Just don't answer me talking about other things except the correct answer or, if something is not clear, a concrete question.

Since my problem is of a more general nature, answers to this concrete two questions may not be applied to other situations. But hopefully, with this concrete questions and concrete solutions to them, I will have a hint of a technique that I can apply to many other similar situations (different commands , different outputs), exactly because I'm considering what Mr C thought I'm not:

> "There is nothing that mandates or suggests that all programs should produce output in exactly the same way. Programs that format their output specifically for *the screen* must make some compromises (wrap or cut)"

Doesn't this make sense or what?

At the end you tell me:
> "me and Mr. C have both told you already that awk doesn't do that -- aptitude formats its output at an 80 char width before it ever gets to awk"

ok so?

then you say:
> "We've also both posted to show you how to address that problem."
I have only read that the option -w in aptitude overrides the 80 char/line output when the output goes to a pipe. How can I put this together with anything else you have said? You have said nothing else. If I use awk in a pipe then I will have exactly the problem I talking about: and I won't extract the whole column in all it's width.

Ok that is an approximation but since my first post I haven't stopped talking about columns, the width of the columns, and extracting a column without loss of data, etc, etc.
But with the -w option of aptitude _we haven't answered_ the simple questions of the imaginary exam with the aptitude command. Let alone the general problem of extracting whole lines of a column. But let's leave that aside and focus only in these two questions a9 and b).


Then you say
> "What you do with that output later on is up to you."

I don't understand why you say this. what has this to do with the "exam" questions or with the problem??
Maybe you say this because I said something about writing the list to a file. Forget about that. That's not the problem. The problem is the List of packages. To Display it or save it in a file is the same problem. I want the List of the Packages. Just that. So I really don't understand what I have to put together with what?
The -w option with what?

Mr C. said:
> ""...Had you asked "how do I get Aptitude's full text description?", you would have received a specific answer."

I'm not sure I understand what he wrote, but if I do, I didn't asked that because the answer to that is not an answer to my problem. What about understanding my problem instead?


At the very end you say:
> "Maybe next time you'd get farther by posting examples of what commands you use, what results you get and what results you want."

As I told you, I can't believe that after my long explanations and super-concrete questions II still need to post the outputs.

Ok.

```
$ aptitude -w $COLUMNS search java | head
p   coco-java                                                     - Coco/R Compiler Generator (Java Version)
p   entity-javascript                                             - XML-based GUI builder for GTK+ (JavaScript bindings)
p   free-java-sdk                                                 - Complete Java SDK environment consisting of free Java tools
p   java-common                                                   - Base of all Java packages
v   java-compiler                                                 -
p   java-gcj-compat                                               - Java runtime environment using GIJ
p   java-gcj-compat-dev                                           - Java runtime environment with GCJ
p   java-gcj-compat-plugin                                        - Web browser plugin to execute Java (tm) applets using gij
p   java-package                                                  - utility for building Java(TM) 2 related Debian packages
v   java-runtime                                                -
```

As you can see, if you scroll to the right, this is not the list  of the first 25 packages from the output of aptitude search java. There is no extraction of any column which is the problem I've been talking about again and again from the very first post.

You wanted concrete questions.I posted them and still haven't seen a concrete answer, but mere scolding. So I really don't know what else I have to do with this output. That is exactly the reason of my starting this thread. I'm exactly in the starting point, except that, as you showed me, I understand where and how some programs decide to format the output according to the nature of the standard output.

---

### Post by tacubuntuforums on 2007-07-16
NETSTAT

As I said, the problem with netstat is different but it has to do with displaying columns in an uncomplete way too.

This time, this is the output:

```
$ netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 casal.upc.es:www        dup-148-221-219-20:1397 SYN_RECV
tcp        0      0 casal.upc.es:www        dup-148-221-219-20:1396 SYN_RECV
tcp        0      0 casal.upc.es:imap2      247.Red-88-15-99.:26663 ESTABLISHED
tcp        0      0 casal.upc.e:netbios-ssn 147.83.156.140:2268     ESTABLISHED
tcp        0      0 casal.upc.es:imap2      fw.l2f.inesc-id.pt:1907 ESTABLISHED
tcp        0      0 casal.upc.es:imap2      147.83.50.104:3889      ESTABLISHED
```

Can you tell me what port is used in the connection on the 4th row?
Sometimes,.. yes only  sometimes, the situation is much worse and you can't figure out what goes in there.
Of course, if you execute the command in your own machine now, you will get a different result  and might get the complete information, because only sometimes the information to be displayed is longer than the column's width. That's why I wrote:

> ... There are some programs that display their output in columns (n the console) but often, the columns are not wide enough so that the data is also cut in some lines, and you can't see the whole information. That happens sometimes, for example, when using netstat:

Upsss...sorry, yes you can see the port in the 4th line, there's only an 's' missing, but, as i said, sometimes the situation is much worse. Do I still need to post the ouput of that exact moment?

---

### Post by tacubuntuforums on 2007-07-17
Another similar example-problem:

[COLOR="Red"]c) Obtain the list of the whole descriptions of all the packages from the output of *dpkg -l* whose corresponding lines contain the string "desk" (in the name of the package or in its description)[/COLOR]


note that
```

dpkg -l | grep desk | cut -c 70-

 and

dpkg -l  *desk* | cut -c 70-
```  are incorrect solutions

---

### Post by Mr. C. on 2007-07-17
You have to be one of the most stubborn people I've experienced in these forums.

```
man dpkg

...

COLUMNS
    Sets the number of columns dpkg should use when displaying formatted text. Currently only used by -l.
```

---

### Post by tacubuntuforums on 2007-07-17
Stubborn? thank you! or thank God!

yet

man dpkg   is _not_ an instruction which solves a), b) or c) as you well know

---

### Post by Mr. C. on 2007-07-17
And you won't be getting much help here.

Don't let the door hit you on the way out...

---

### Post by tacubuntuforums on 2007-07-18
OH my....!  

Mike, I have posted these clear, simple and concrete questions to start tackling this little problem I often come across.
If you know a correct answer to these example problems and you can let the real "Ubuntu spirit" be with you, then show it to us; if not, why don't you just keep your hateful remarks for yourself and refrain your desire to offend me. It's very easy!

---

### Post by tacubuntuforums on 2007-08-30
Anyone else knows a  solution or workaround to this small problem?

---

