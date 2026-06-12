---
title: "Reading a field from $ps u"
date: 2008-07-08
forum: General Help
---

### Post by kaede1010 on 2008-07-08
Hi all i'm very very new to UBuntu and C/C++ programming and would appreciate any help. Firstly, my goal is to pipe $ps u through a filter and display the appropriate output. for example, i would like to see the the filter program reading the number of S,T,R processes and calculate the total number when i type $ps u|./myfilter where myfilter is the name of my program. How do i go about doing this?

---

### Post by HalPomeranz on 2008-07-08
You can do this with a series of shell commands:

```

ps u | awk '{ print $8 }' | cut -c1 | sort | uniq -c

```

The "awk ..." bit prints the 8th column of output from "ps u", which is the "STAT" column.  "cut -c1" cuts out just the first character (S, R, etc).  "sort" groups the characters by type and "uniq -c" prints a count of each unique character.

And this is why the Linux/Unix command line kicks serious butt...

---

### Post by kaede1010 on 2008-07-09
thanks for the reply bro... but my assignment requires me to strictly use $ps u|./filter.out where filter.out is my written filter program...

a section of my coding looks like this

#include <iostream>
using namespace std;
int main(int argc, char* argv)
{
	char mystring[128];
	while ( cin >> mystring )
	{
	cout << mystring << endl;
	}
	return 0;
}

and when i type $ps u|./filter.out at the command line, it forms everything into a single column starting from left to right i think. is there anyway i can modify my codings such that it reads the input and displays the figures in the below format

1)The number of processes in S (Sleep) mode			?
2)The number of processes in T (Stopped) mode			?
3)The number of processes in R (Runnable) mode			?
4)The Total Virtual Memory size occupied by all processes is: ???
5)The running processes are :???				

where ??? are the information i need to find out using codings in the filter.out program. Any idea? any help appreciated thanks!

---

