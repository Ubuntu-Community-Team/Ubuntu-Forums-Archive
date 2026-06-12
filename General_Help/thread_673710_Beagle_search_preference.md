---
title: "Beagle search preference"
date: 2008-01-20
forum: General Help
---

### Post by dplecto on 2008-01-20
hey all,
 
            I wasn't sure where to post this so here it goes. I have recently installed beagle and it seems to be working great. The problem I am running into is that if my search query pulls out a huge number of results, bealge displays only the top few  results.

          How do i see the other result ???
                         
                       Most of the time, the result i am looking for is not shown by beagle by terming them irrelevant - it is me who is going to determine which is irrelevant and which is not.

 I searched in the config files in ~/.beagle directory but couldn't find anything relevant.

 I started beagle since it seemed to be the faster way considering that i have more then 500 gigs of data and using my favourite find command doesn't make sense - unless i have too much time in my hand and  i don't.

Does anyone know a way to get this done ? 

Thanks,

---

### Post by dbera on 2008-01-21
What do you mean by saying only the top results are displayed ? The results are displayed page by page and there are arrows to display the next/previous set of results.

---

### Post by dplecto on 2008-01-21
nah ...........for example, if you enter a search query like " *.avi", on the bottom it says - 
" Showing the top 94 of 208 total matches".

If you see all the pages, then there will be only 94 hits shown not all the 208. 

You are right, when you use a query that pulls out small number of hits, all are shown page by page
But with querys that pull out a lot of hits, that is not the case.

My beagle version: 0.2.16.3

Ubuntu 7.10

---

### Post by dbera on 2008-01-21
Oh ... 0.2.16 (IIRC) had a problem where some of the correct results would not be shown. It was fixed in 0.2.17+. But even the latest version would not help much since beagle-search caps a maximum of 100 results while displaying. The idea is its costly to display lots of results, and if there are lots of results then the user is better off in rewriting the query to narrow the search scope (similar to what google search does, they cap at 1000).

---

### Post by dplecto on 2008-01-22
hmmm............. I was attempting to list all the files with a say a certain extension or a phrase in file name. But, if the limitation is hard coded within the beagle, I will stick with the trusty "find" command. Probably will write a small shell script so that I won't have to type in all the options each time i have to use it but, at least it gives me all the result I want. 

Rather see all then miss something. Still, beagle is a handy utility for quick searches. It would have been better if there was a way to define the limitation by user themselves (using the config files).............

---

### Post by dbera on 2008-01-22
If you are only looking for files with certain names or extension, find or locate is a much better option. Beagle would be an overkill if you dont search for file content. If you do insist and dont mind command line you can use beagle-query which has an option to override the limit, but again that is an overkill compared to find/locate.

---

