---
title: "Upstart job: Run task once per event instead of just once"
date: 2012-11-25
forum: General Help
---

### Post by Beacon11 on 2012-11-25
Note: I asked this question here without an answer: [http://askubuntu.com/questions/221196/upstart-job-run-task-once-per-event](http://askubuntu.com/questions/221196/upstart-job-run-task-once-per-event) .

I'm a little confused regarding how jobs start on Upstart events. To illustrate my misunderstanding, I have four Upstart jobs that look like the following:

Job 1:
```

start on local-filesystems

task

script
    echo "job 1 ran" >> /tmp/job1
end script

```

Job 2:

```
start on (local-filesystems and net-device-added)

task

script
    echo "job 2 ran" >> /tmp/job2
end script
```

Job 3:

```
start on (local-filesystems and bluetooth-device-added)

task

script
    echo "job 3 ran" >> /tmp/job3
end script
```

Job 4:

```
start on local-filesystems or (local-filesystems and net-device-added) or (local-filesystems and bluetooth-device-added)

task

script
    echo "job 4 ran" >> /tmp/job4
end script
```

I expect the following file contents after a reboot:

/tmp/job1:

```
job 1 ran
```

/tmp/job2:

```
job 2 ran
```

/tmp/job3:

```
job 3 ran
```

/tmp/job4:

```
job 4 ran
job 4 ran
job 4 ran
```

I expect Job 4 to have ran three times because it can be started by three separate sets of events, all of which occur as proven by the other jobs. But my expectations are incorrect; the files actually contain the following:

/tmp/job1:

```
job 1 ran
```

/tmp/job2:

```
job 2 ran
```

/tmp/job3:

```
job 3 ran
```

/tmp/job4:

```
job 4 ran
```

Why is job4 only being run once, even though all three sets of events are occurring? Is there any way to achieve the behavior of running this job whenever any of the signals occur, regardless of how many times the job actually runs? If it helps, I edited it to print out the $UPSTART_EVENTS variable to see what events are causing job 4, and it's local-filesystems.

To summarize: I would like job 4 to run on the local-filesystems event, AND on the net-device-added event (as long as local_filesystems has occurred as well), AND on the bluetooth-device-added event (as long as local_filesystems has occurred). How do I make that happen?

Thank you!

---

