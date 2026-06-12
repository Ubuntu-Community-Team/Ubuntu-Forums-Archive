---
title: "Insert Data Using Awk"
date: 2018-12-23
forum: General Help
---

### Post by eusanpe on 2018-12-23
Hello all,

I am hoping someone can help me insert data from a file into another file. The files I have contain the following data...

> Description:
This is a description test
This is a description test2
;;

Summary:
This is a test
This is a second test
This is a third test
;;

Keywords: data, data1
;;

I would like to insert data after the line "Summary:" and before the ";;". The data between "Summary" and ";;" is not static
so it can contain multiple lines. In the example above there are only 3 lines.

It would look like:

> Description:
This is a description test
This is a description test2
;;

Summary:
This is a test
This is a second test
This is a third test

Date		Modified by
----------------------------------
12/21/2018	Tony P.
;;

Keywords: data, data1
;;

If I run the awk command I get the following:

> awk '/explanation:/,/;;/' temp | cat -n

     1		explanation:  
     2		This is a test
     3		this is a test2
     4		this is a test3
     5		;;


awk '/explanation:/{f=1;next} /;;/{f=0} f' temp
	This is a test
	this is a test2
	this is a test3


I have a few hundred files that I need to modify and this would be a alot easier than doing them one by one. I have tried different things but
I can't get it to work. Any advice is greatly appreciated.

Thanks,
Tony

---

