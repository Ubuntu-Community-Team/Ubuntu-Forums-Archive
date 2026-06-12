---
title: "Can you tell me how this program run"
date: 2006-12-01
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-01
#include<stdio.h>
main()
{
	int c;        
	while(c=getchar()!=EOF)
		printf("%d\n",c); 
	printf("%d - at EOF\n",c);
}
Can you explain this program?
Can you analyze this program for me?Please tell me .ok?:KS

---

### Post by Rinzwind on 2006-12-01
I think it looks like a bashscript.

Save the text as a file. 
Goto Terminal and the directory where it's located.
type
chmod 777 {file_name}
and execute it with
./{filename}

---

### Post by lloyd_b on 2006-12-01
No, it's NOT a bash script - it's a very simple C program.

To compile the program:

"gcc -o {outfile} {filename}"

Where {outfile} is the name you want for the compiled program, and {filename} is the name of the file.

Then, in that directory type "./{outfile}", where {outfile} is the name you told it to use above.

The program just echoes whatever characters are typed in (looks like something from an "Introduction to C Programming" type book/web page).

Lloyd B.

---

### Post by LaoLiulaoliu on 2006-12-01
when I execute it ,it show as follows:
a /*I type a*/
1
1
0 - at EOF:KS

---

### Post by lloyd_b on 2006-12-01
First, I misread the code (it's supposed to output the ASCII value for each character, not echo the character).

Second, you're missing some parentheses in the "if" statement.

Try changing 

while(c=getchar()!=EOF)

To

while ((c = getchar()) != EOF)

and the results will look like this:

./{program}
abcd<return>
97
98
99
100
10

Lloyd B.

---

