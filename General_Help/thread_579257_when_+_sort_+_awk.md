---
title: "when + sort + awk"
date: 2007-10-18
forum: General Help
---

### Post by karvec on 2007-10-18
Ok, so I was using when, a simple calendar program.  I was getting tired of Evolution, because it's not as simple as I want, and I searched and ended up with when....

And something when doesn't do is sort by time.  It just sorts by the date.  The date format is:

Oct 18 2007, <your text here>
...

And I've been using 
sort -nk 1.14 -o /home/karvec/.when/calendar

to sort:

Oct 18 2007, 0800-1000 PT
Oct 18 2007, 1030-1500 Work
etc., etc..

And I was wondering {since it gets messy with all the dates out of order in my calendar file, it starts to look a little jumbled...}  if there was a way to sort by the day, then the time using some combination of sort or something.  I want to be able to run it as a shell script to sort it by time and date so that when i edit the file, I can find which date I need easily.

If anyone has any ideas or knows exactly how to do it, please show me and explain.  I'm a newbie.  Heck, I barely figured out the sort thing.  Still not sure how it works.  :P

Thanks to all~~

~~Karvec

---

### Post by stylishpants on 2007-10-18
Instead of trying to cook up something in awk that handles dates and times properly, I'd prefer to use a proper dynamic language like perl, python or ruby since these languages include libraries that can parse date strings really well.

Here's a ruby solution, with the parsing of your date string being done by ruby's standard Time class:
```

fhanson@fhanson:/tmp$ cat file
Oct 18 2007, 1030-1500 Work
Oct 17 2007, 1030-1500 Work
Oct 18 2007, 0930-1000 PT
Oct 17 2007, 0800-1000 PT
Oct 18 2007, 0800-1000 PT
Oct 18 2007, 0000-1500 Work

fhanson@fhanson:/tmp$ cat file | ruby -rtime -e 'print $stdin.readlines.map{|str| t=Time::parse(str); [t,str]}.sort.map{|a| a[1]}'
Oct 17 2007, 0800-1000 PT
Oct 17 2007, 1030-1500 Work
Oct 18 2007, 0000-1500 Work
Oct 18 2007, 0800-1000 PT
Oct 18 2007, 0930-1000 PT
Oct 18 2007, 1030-1500 Work
fhanson@fhanson:/tmp$ 


```

---

### Post by karvec on 2007-10-18
I love you.  Now explain it.  :P  And how do I save it to the file?  It just outputs to terminal, correct?  I am not familiar with ruby, I'm barely familiar with C, and never used perl or python...  or ruby.  :P

---

### Post by stylishpants on 2007-10-18
Ugh, I messed up.

The previous solution looked right but was not quite correct.  Here's a fixed version.

```

ruby -rtime -e 'print ARGF.readlines.sort_by{|str| s=str.sub(/, \d\d/,"\\0:").sub(/-.*/,""); Time.parse(s)}' file

```


Explanation:
# Run the ruby interpreter, require the 'time' library, execute the following ruby code string
 ruby -rtime -e  '...'  

# Read in all input lines from stdin, and store them in a ruby array
ARGF.readlines

# sort the array of lines.  For each string in the array, run the following code block on the string
# and save the resulting ruby object.  Then sort the array of lines by comparing the 
# resulting objects.
.sort_by{|str|
...
}


# Modify the input string a bit so that the time parsing code will understand it
#
#  The input string looks like this:
#      Oct 18 2007, 1030-1500 Work
#
#  We want it to look like this: (add a colon, strip everything after the start time)
#      Oct 18 2007, 10:30
#
# The String::sub method does string substitutions (like s/// in perl.)  The first call to 'sub' adds a 
# comma after the first 2 digits that come after the first comma.  The second call to 'sub' strips off 
# the first - character and everything that follows it.
#
# The result is stored in a variable named 's'
s=str.sub(/, \d\d/,"\\0:").sub(/-.*/,"");

# Now use ruby's Time class to parse the modified string.
# Since this is the last thing in the {} code block, the newly created Time object returned by this 
# call will be used by the 'sort_by' function for sorting.
Time.parse(s)


# The overall structure is much clearer if you leave out the code in the middle with all the regular expressions
# that just modifies the string:
```
ruby -rtime -e 'print ARGF.readlines.sort_by{|str| Time.parse(str)}' file
```


OK, that's the explanation of the code.

Redirect the output to a file by appending this on to the end of the command:
```

> file

```
This redirects the output to a file named 'file'.  Beware: If a file named 'file' already exists, you will silently overwrite it.

---

### Post by stylishpants on 2007-10-19
If you're new to this sort of thing then maybe a one-liner isn't the best thing for you, especially if this is a task you will want to do again.

Here's a script that takes care of the entire problem from start to finish -- it reads in the file, sorts the lines, and writes the result back to the original file.

Lots of comments, in case you want to modify it.

```
#!/usr/bin/ruby -w

# Purpose: Sort a 'when' calendar file by date and time
# Date:    2007-10-19 

require 'time' 
require 'ftools' 

# Take input file name from the command line
filename = ARGV.shift
if filename.nil?
	puts "You must enter the name of a file to modify on the command line."
	exit 1
end
raise "No such file: #{filename}" unless File.exist? filename

# Read in the input file
lines = IO.readlines(filename)


# Sort the array of lines by time
lines = lines.sort_by { |str|

	# Make a copy of the string so we don't modify the original
	s = str.clone

	# Add a colon to the middle of the 4-digit time
	# 	before: Oct 18 2007, 1030-1500 Work
	# 	after:  Oct 18 2007, 10:30-1500 Work
	s.sub!(/, \d\d/, '\0:')

	# Strip everything after the start time
	# 	before: Oct 18 2007, 10:30-1500 Work
	# 	after:  Oct 18 2007, 10:30
	s.sub!(/-.*/, '')

	# Time library is able to parse what remains
	Time.parse(s)
}


# Make a backup copy of the original file
File::copy(filename, filename + ".bak")

# Update the original file with the sorted lines
File::open(filename,"w") { |io| io << lines }


```

---

### Post by karvec on 2007-10-19
Thanks alot for all your time!  I'm going to spend some time learning Ruby now, too--  Learning C in a classroom environment right now, and it's some of the best education I've had.  Granted, it's not complicated at the moment, but it's pretty darn fun.

~~karvec

---

