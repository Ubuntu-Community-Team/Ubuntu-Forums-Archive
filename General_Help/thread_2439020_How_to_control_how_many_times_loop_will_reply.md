---
title: "How to control how many times loop will reply ?"
date: 2020-03-21
forum: General Help
---

### Post by alex346 on 2020-03-21
Long time ago I have used in my script:


```
for i in `ls  /directory`                                                                                                                                                                      
do  command &
done            

```


And that working, but as the files qty increased I am getting OOM errors as that command starts all occurencies in one time.


I would like to find any way to limit number of parallel loop runs:


[B]Like run the loop 5 times, when one of the occurencies will finish, andd another one, and after that add next one, or two, or any number to keep 5 concurrent
[/B]


Is that possible ? That is the script which I am using to make lot of connections to remote storage - overnight I would utilise 100% of tunnel bandwith and the 'command' doesn't support multithreading :(.


Yeah, I see parallel package, but I can't change this scripts :(


regards

---

### Post by norobro on 2020-03-22
> **alex346 said:**
> ... , but I can't change this scripts :(Not sure what you mean by this.  The following is no help if you can't change your scripts.

Can't find a way to link to a specific answer but the job_limit function from the post about two-thirds of the way down the page (5 upvotes) at this link works:  [https://stackoverflow.com/questions/1537956/bash-limit-the-number-of-concurrent-jobs#id=%22comment-99994766%22](https://stackoverflow.com/questions/1537956/bash-limit-the-number-of-concurrent-jobs#id=%22comment-99994766%22)


My test files 
script.sh:```
#!/bin/bash 

source job_limit.sh  # job_limit() copied from link

for i in $(ls $1)
  do 
       ./command.sh $i &   # put your executable here
        job_limit 4 # run 4 jobs concurrently
  done
```job_limit.sh```
job_limit () {    # Test for single positive integer input
    if (( $# == 1 )) && [[ $1 =~ ^[1-9][0-9]*$ ]]
    then


        # Check number of running jobs
        joblist=($(jobs -rp))
        while (( ${#joblist
[*]} >= $1 ))
        do


            # Wait for any job to finish
            command='wait '${joblist[0]}
            for job in ${joblist[@]:1}
            do
                command+=' || wait '$job
            done
            eval $command
            joblist=($(jobs -rp))
        done
   fi
}
```command.sh```
x=$(((RANDOM % 10) + 1)) # stagger sleep times
echo "running $1 $x"
sleep $(($x))
```As soon as a sleep times out, command.sh is run with the next file:```
$ ./script.sh 
running command.sh 10
running job_limit.sh 2
running test_file 9
running test_file1 2
running script.sh 5
running test_file2 9

```

---

