---
title: "bash, xargs, arguments to my program"
date: 2015-05-18
forum: General Help
---

### Post by gam01hr on 2015-05-18
Hello,
I have a long file that includes 8 values on a line.
```

$ cat myfile.txt
732   732   731   732   732   732   732   732
733   732   732   732   732   732   732   732
732   732   732   732   732   732   732   732
731   731   731   731   731   731   731   731
731   731   731   731   731   731   731   731

```
Then I have a simple program that prints 8 arguments.
```

// main.c
// this program accept 8 arguments only and do simple print
// in future it will do some useful calculation on arguments
//
int main ( int argc, char *argv[] )
{

  if (argc!=9)
  {
      printf("use 8 arguments only");
      return(1);
  }
  else
  {
      printf("%s %s %s %s %s %s %s %s\n",\
     argv[1],argv[2],argv[3],argv[4],argv[5],argv[6],argv[7],argv[8]);
     return(0);
  }
}

```
My intention is to read a line from file (myfile.txt) and pass the numbers as the arguments to program (main.exe). I want to call (main.exe) for every line to process it.
```

$ grep '^.'  myfile.txt | head --lines=1 | xargs ./main.exe
732 732 731 732 732 732 732 732

```
This command works fine. The problem is it works only for one line. 
```

$ grep '^.'  myfile.txt | xargs ./main.exe
use 8 arguments only

```
This code doesn't work as expected.

Please would you advice me how to solve it? Thx

---

### Post by steeldriver on 2015-05-18
You need the -n (--max-args) option, I think. From man xargs

```

       --max-args=max-args
       -n max-args
              Use  at  most  max-args  arguments per command line.  Fewer than
              max-args arguments will be used if the size (see the -s  option)
              is  exceeded, unless the -x option is given, in which case xargs
              will exit.

```

Also, the grep is unnecessary - xargs can read arguments from a file

```

       --arg-file=file
       -a file
              Read items from file instead of standard input.  If you use this
              option, stdin remains unchanged when commands are  run.   Other&#8208;
              wise, stdin is redirected from /dev/null.

```

So
```

xargs -a myfile.txt -n 8 ./main.exe

```

---

### Post by sisco311 on 2015-05-18
Check out BashFAQ 001 (link in my signature):
```
while read -r line
do
    main.exe $line
done < myfile.txt
```

---

