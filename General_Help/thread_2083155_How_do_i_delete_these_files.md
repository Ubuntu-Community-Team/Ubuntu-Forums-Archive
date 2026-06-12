---
title: "How do i delete these files?"
date: 2012-11-11
forum: General Help
---

### Post by dan0804smith on 2012-11-11
I ran this command: 

sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
   

This was my output:  ```

100M    /root/.local/share/Trash/files/recup_dir.2.30
100M    /root/.local/share/Trash/files/recup_dir.2.72
100M    /root/.local/share/Trash/files/recup_dir.32
101M    /root/.local/share/Trash/files/recup_dir.2.27
101M    /root/.local/share/Trash/files/recup_dir.29
103M    /root/.local/share/Trash/files/recup_dir.2.7
103M    /root/.local/share/Trash/files/recup_dir.9
103M    /root/.local/share/Trash/files/recup_dir.93
106M    /root/.local/share/Trash/files/recup_dir.187
106M    /root/.local/share/Trash/files/recup_dir.71
107M    /root/.local/share/Trash/files/recup_dir.131
107M    /root/.local/share/Trash/files/recup_dir.136
107M    /root/.local/share/Trash/files/recup_dir.2.46
107M    /root/.local/share/Trash/files/recup_dir.51
108M    /root/.local/share/Trash/files/recup_dir.106
108M    /root/.local/share/Trash/files/recup_dir.2.78
108M    /root/.local/share/Trash/files/recup_dir.52
109M    /root/.local/share/Trash/files/recup_dir.2.32
109M    /root/.local/share/Trash/files/recup_dir.34
110M    /root/.local/share/Trash/files/recup_dir.2.28
110M    /root/.local/share/Trash/files/recup_dir.2.53
110M    /root/.local/share/Trash/files/recup_dir.30
110M    /root/.local/share/Trash/files/recup_dir.55
110M    /root/.local/share/Trash/files/recup_dir.89
112M    /root/.local/share/Trash/files/recup_dir.2.31
112M    /root/.local/share/Trash/files/recup_dir.33
114M    /root/.local/share/Trash/files/recup_dir.2.29
114M    /root/.local/share/Trash/files/recup_dir.2.74
114M    /root/.local/share/Trash/files/recup_dir.31
115M    /root/.local/share/Trash/files/recup_dir.125
117M    /root/.local/share/Trash/files/recup_dir.83
118M    /root/.local/share/Trash/files/recup_dir.105
118M    /root/.local/share/Trash/files/recup_dir.2.70
119M    /root/.local/share/Trash/files/recup_dir.133
1.1G    /root/.local/share/Trash/files/recup_dir.148
11M    /root/.local/share/Trash/files/recup_dir.179
1.1M    /root/.local/share/Trash/info
122M    /root/.local/share/Trash/files/recup_dir.80
124M    /root/.local/share/Trash/files/recup_dir.137
125G    /root/.local/share/Trash
125G    /root/.local/share/Trash/files
125M    /root/.local/share/Trash/files/recup_dir.2.49
129M    /root/.local/share/Trash/files/recup_dir.153
1.2G    /root/.local/share/Trash/files/recup_dir.165
1.2G    /root/.local/share/Trash/files/recup_dir.166
12K    /media/A80E1DE60E1DAE76/.Trash-1000/files
12M    /root/.local/share/Trash/files/recup_dir.178
12M    /root/.local/share/Trash/files/recup_dir.180
12M    /root/.local/share/Trash/files/recup_dir.181
130M    /root/.local/share/Trash/files/recup_dir.85
137M    /root/.local/share/Trash/files/recup_dir.2.5
137M    /root/.local/share/Trash/files/recup_dir.7
137M    /root/.local/share/Trash/files/recup_dir.76
13M    /root/.local/share/Trash/files/recup_dir.143
13M    /root/.local/share/Trash/files/recup_dir.18
13M    /root/.local/share/Trash/files/recup_dir.182
13M    /root/.local/share/Trash/files/recup_dir.2.16
13M    /root/.local/share/Trash/files/recup_dir.2.2
13M    /root/.local/share/Trash/files/recup_dir.4
140M    /root/.local/share/Trash/files/recup_dir.2.77
145M    /root/.local/share/Trash/files/recup_dir.2.63
147M    /root/.local/share/Trash/files/recup_dir.2.43
147M    /root/.local/share/Trash/files/recup_dir.45
148M    /root/.local/share/Trash/files/recup_dir.84
149M    /root/.local/share/Trash/files/recup_dir.160
149M    /root/.local/share/Trash/files/recup_dir.2.79
1.4G    /root/.local/share/Trash/files/recup_dir.191
150M    /root/.local/share/Trash/files/recup_dir.2.26
150M    /root/.local/share/Trash/files/recup_dir.28
153M    /root/.local/share/Trash/files/recup_dir.64
153M    /root/.local/share/Trash/files/recup_dir.78
154M    /root/.local/share/Trash/files/recup_dir.107
155M    /root/.local/share/Trash/files/recup_dir.2.80
155M    /root/.local/share/Trash/files/recup_dir.79
15M    /root/.local/share/Trash/files/recup_dir.151
162M    /root/.local/share/Trash/files/recup_dir.65
163M    /root/.local/share/Trash/files/recup_dir.82
164M    /root/.local/share/Trash/files/recup_dir.104
165M    /root/.local/share/Trash/files/recup_dir.2.39
165M    /root/.local/share/Trash/files/recup_dir.41
168M    /root/.local/share/Trash/files/recup_dir.2.62
16M    /root/.local/share/Trash/files/recup_dir.171
170M    /root/.local/share/Trash/files/recup_dir.135
170M    /root/.local/share/Trash/files/recup_dir.159
171M    /root/.local/share/Trash/files/recup_dir.91
172M    /root/.local/share/Trash/files/recup_dir.2.41
172M    /root/.local/share/Trash/files/recup_dir.43
175M    /root/.local/share/Trash/files/recup_dir.2.33
175M    /root/.local/share/Trash/files/recup_dir.35
176M    /root/.local/share/Trash/files/recup_dir.2.76
179M    /root/.local/share/Trash/files/recup_dir.2.38
179M    /root/.local/share/Trash/files/recup_dir.40
179M    /root/.local/share/Trash/files/recup_dir.61
1.7G    /root/.local/share/Trash/files/recup_dir.167
17M    /root/.local/share/Trash/files/recup_dir.172
180M    /root/.local/share/Trash/files/recup_dir.186
181M    /root/.local/share/Trash/files/recup_dir.2.71
182M    /root/.local/share/Trash/files/recup_dir.158
183M    /root/.local/share/Trash/files/recup_dir.2.59
185M    /root/.local/share/Trash/files/recup_dir.123
189M    /root/.local/share/Trash/files/recup_dir.92
18M    /root/.local/share/Trash/files/recup_dir.142
18M    /root/.local/share/Trash/files/recup_dir.149
18M    /root/.local/share/Trash/files/recup_dir.150
18M    /root/.local/share/Trash/files/recup_dir.152
18M    /root/.local/share/Trash/files/recup_dir.173
18M    /root/.local/share/Trash/files/recup_dir.177
191M    /root/.local/share/Trash/files/recup_dir.147
193M    /root/.local/share/Trash/files/recup_dir.102
195M    /root/.local/share/Trash/files/recup_dir.73
196M    /root/.local/share/Trash/files/recup_dir.94
198M    /root/.local/share/Trash/files/recup_dir.2.58
19M    /root/.local/share/Trash/files/recup_dir.175
19M    /root/.local/share/Trash/files/recup_dir.176
205M    /root/.local/share/Trash/files/recup_dir.108
206M    /root/.local/share/Trash/files/recup_dir.56
206M    /root/.local/share/Trash/files/recup_dir.60
207M    /root/.local/share/Trash/files/recup_dir.2.55
209M    /root/.local/share/Trash/files/recup_dir.90
2.0G    /root/.local/share/Trash/files/recup_dir.190
20K    /media/A80E1DE60E1DAE76/.Trash-1000/info
20M    /root/.local/share/Trash/files/recup_dir.17
20M    /root/.local/share/Trash/files/recup_dir.2.15
210M    /root/.local/share/Trash/files/recup_dir.121
211M    /root/.local/share/Trash/files/recup_dir.134
212M    /root/.local/share/Trash/files/recup_dir.57
21M    /root/.local/share/Trash/files/recup_dir.174
223M    /root/.local/share/Trash/files/recup_dir.88
225M    /root/.local/share/Trash/files/recup_dir.118
230M    /root/.local/share/Trash/files/recup_dir.87
232M    /root/.local/share/Trash/files/recup_dir.66
235M    /root/.local/share/Trash/files/recup_dir.139
236M    /root/.local/share/Trash/files/recup_dir.97
238M    /root/.local/share/Trash/files/recup_dir.2.54
240M    /root/.local/share/Trash/files/recup_dir.163
241M    /root/.local/share/Trash/files/recup_dir.126
242M    /root/.local/share/Trash/files/recup_dir.2.81
243M    /root/.local/share/Trash/files/recup_dir.156
244M    /root/.local/share/Trash/files/recup_dir.2.37
244M    /root/.local/share/Trash/files/recup_dir.39
248M    /root/.local/share/Trash/files/recup_dir.110
249M    /root/.local/share/Trash/files/recup_dir.75
256M    /root/.local/share/Trash/files/recup_dir.2.73
257M    /root/.local/share/Trash/files/recup_dir.2.64
25M    /root/.local/share/Trash/files/recup_dir.10
25M    /root/.local/share/Trash/files/recup_dir.2.8
262M    /root/.local/share/Trash/files/recup_dir.86
266M    /root/.local/share/Trash/files/recup_dir.144
27M    /root/.local/share/Trash/files/recup_dir.99
282M    /root/.local/share/Trash/files/recup_dir.127
29M    /root/.local/share/Trash/files/recup_dir.183
29M    /root/.local/share/Trash/files/recup_dir.22
29M    /root/.local/share/Trash/files/recup_dir.2.20
316M    /root/.local/share/Trash/files/recup_dir.124
31M    /root/.local/share/Trash/files/recup_dir.2.21
31M    /root/.local/share/Trash/files/recup_dir.23
320M    /root/.local/share/Trash/files/recup_dir.168
32M    /root/.local/share/Trash/files/recup_dir.12
32M    /root/.local/share/Trash/files/recup_dir.2.10
334M    /root/.local/share/Trash/files/recup_dir.140
338M    /root/.local/share/Trash/files/recup_dir.69
33M    /root/.local/share/Trash/files/recup_dir.21
33M    /root/.local/share/Trash/files/recup_dir.2.19
340M    /root/.local/share/Trash/files/recup_dir.2.57
341M    /root/.local/share/Trash/files/recup_dir.185
342M    /root/.local/share/Trash/files/recup_dir.169
343M    /root/.local/share/Trash/files/recup_dir.129
346M    /root/.local/share/Trash/files/recup_dir.111
348M    /root/.local/share/Trash/files/recup_dir.103
351M    /root/.local/share/Trash/files/recup_dir.2.34
351M    /root/.local/share/Trash/files/recup_dir.36
352M    /root/.local/share/Trash/files/recup_dir.155
358M    /root/.local/share/Trash/files/recup_dir.59
36G    /root/.local/share/Trash/files/recup_dir.1
36G    /root/.local/share/Trash/files/recup_dir.2
36M    /root/.local/share/Trash/files/recup_dir.120
36M    /root/.local/share/Trash/files/recup_dir.2.24
36M    /root/.local/share/Trash/files/recup_dir.2.51
36M    /root/.local/share/Trash/files/recup_dir.26
37M    /root/.local/share/Trash/files/recup_dir.112
390M    /root/.local/share/Trash/files/recup_dir.162
398M    /root/.local/share/Trash/files/recup_dir.2.67
39M    /root/.local/share/Trash/files/recup_dir.145
401M    /root/.local/share/Trash/files/recup_dir.2.52
402M    /root/.local/share/Trash/files/recup_dir.54
408M    /root/.local/share/Trash/files/recup_dir.2.40
408M    /root/.local/share/Trash/files/recup_dir.42
4.0K    /home/daniel/.local/share/Trash
40K    /media/A80E1DE60E1DAE76/.Trash-1000
41M    /root/.local/share/Trash/files/recup_dir.13
41M    /root/.local/share/Trash/files/recup_dir.2.11
428M    /root/.local/share/Trash/files/recup_dir.2.61
434M    /root/.local/share/Trash/files/recup_dir.2.36
434M    /root/.local/share/Trash/files/recup_dir.38
43M    /root/.local/share/Trash/files/recup_dir.19
43M    /root/.local/share/Trash/files/recup_dir.2.17
43M    /root/.local/share/Trash/files/recup_dir.53
440M    /root/.local/share/Trash/files/recup_dir.157
448M    /root/.local/share/Trash/files/recup_dir.2.35
448M    /root/.local/share/Trash/files/recup_dir.37
44M    /root/.local/share/Trash/files/recup_dir.20
44M    /root/.local/share/Trash/files/recup_dir.2.18
454M    /root/.local/share/Trash/files/recup_dir.116
47M    /root/.local/share/Trash/files/recup_dir.11
47M    /root/.local/share/Trash/files/recup_dir.2.9
48M    /root/.local/share/Trash/files/recup_dir.2.48
495M    /root/.local/share/Trash/files/recup_dir.192
49M    /root/.local/share/Trash/files/recup_dir.114
49M    /root/.local/share/Trash/files/recup_dir.50
52M    /root/.local/share/Trash/files/recup_dir.3
538M    /root/.local/share/Trash/files/recup_dir.2.68
53M    /root/.local/share/Trash/files/recup_dir.95
54M    /root/.local/share/Trash/files/recup_dir.98
551M    /root/.local/share/Trash/files/recup_dir.63
57M    /root/.local/share/Trash/files/recup_dir.101
5.7M    /root/.local/share/Trash/files/recup_dir.119
57M    /root/.local/share/Trash/files/recup_dir.14
57M    /root/.local/share/Trash/files/recup_dir.2.12
581M    /root/.local/share/Trash/files/recup_dir.70
586M    /root/.local/share/Trash/files/recup_dir.170
588M    /root/.local/share/Trash/files/recup_dir.62
58M    /root/.local/share/Trash/files/recup_dir.2.4
58M    /root/.local/share/Trash/files/recup_dir.2.42
58M    /root/.local/share/Trash/files/recup_dir.44
58M    /root/.local/share/Trash/files/recup_dir.6
59M    /root/.local/share/Trash/files/recup_dir.2.22
59M    /root/.local/share/Trash/files/recup_dir.24
603M    /root/.local/share/Trash/files/recup_dir.109
60M    /root/.local/share/Trash/files/recup_dir.15
60M    /root/.local/share/Trash/files/recup_dir.2.13
619M    /root/.local/share/Trash/files/recup_dir.154
61M    /root/.local/share/Trash/files/recup_dir.2.23
61M    /root/.local/share/Trash/files/recup_dir.25
626M    /root/.local/share/Trash/files/recup_dir.138
62M    /root/.local/share/Trash/files/recup_dir.2.3
62M    /root/.local/share/Trash/files/recup_dir.5
63M    /root/.local/share/Trash/files/recup_dir.188
64M    /root/.local/share/Trash/files/recup_dir.2.1
65M    /root/.local/share/Trash/files/recup_dir.113
65M    /root/.local/share/Trash/files/recup_dir.146
69M    /root/.local/share/Trash/files/recup_dir.122
701M    /root/.local/share/Trash/files/recup_dir.2.60
71M    /root/.local/share/Trash/files/recup_dir.130
71M    /root/.local/share/Trash/files/recup_dir.141
72M    /root/.local/share/Trash/files/recup_dir.132
72M    /root/.local/share/Trash/files/recup_dir.2.47
74M    /root/.local/share/Trash/files/recup_dir.16
74M    /root/.local/share/Trash/files/recup_dir.2.14
74M    /root/.local/share/Trash/files/recup_dir.2.25
74M    /root/.local/share/Trash/files/recup_dir.2.45
74M    /root/.local/share/Trash/files/recup_dir.27
74M    /root/.local/share/Trash/files/recup_dir.47
751M    /root/.local/share/Trash/files/recup_dir.164
752M    /root/.local/share/Trash/files/recup_dir.128
76M    /root/.local/share/Trash/files/recup_dir.49
77M    /root/.local/share/Trash/files/recup_dir.115
77M    /root/.local/share/Trash/files/recup_dir.77
8.0K    /media/A80E1DE60E1DAE76/.Trash-1000/expunged
810M    /root/.local/share/Trash/files/recup_dir.58
815M    /root/.local/share/Trash/files/recup_dir.2.66
818M    /root/.local/share/Trash/files/recup_dir.2.56
82M    /root/.local/share/Trash/files/recup_dir.2.44
82M    /root/.local/share/Trash/files/recup_dir.46
835M    /root/.local/share/Trash/files/recup_dir.68
84M    /root/.local/share/Trash/files/recup_dir.189
860M    /root/.local/share/Trash/files/recup_dir.161
86M    /root/.local/share/Trash/files/recup_dir.117
86M    /root/.local/share/Trash/files/recup_dir.2.69
86M    /root/.local/share/Trash/files/recup_dir.2.75
90M    /root/.local/share/Trash/files/recup_dir.74
924M    /root/.local/share/Trash/files/recup_dir.184
94M    /root/.local/share/Trash/files/recup_dir.81
95M    /root/.local/share/Trash/files/recup_dir.100
96M    /root/.local/share/Trash/files/recup_dir.2.6
96M    /root/.local/share/Trash/files/recup_dir.2.65
96M    /root/.local/share/Trash/files/recup_dir.8
97M    /root/.local/share/Trash/files/recup_dir.2.50
97M    /root/.local/share/Trash/files/recup_dir.67
97M    /root/.local/share/Trash/files/recup_dir.72
98M    /root/.local/share/Trash/files/recup_dir.96
99M    /root/.local/share/Trash/files/recup_dir.48
```

How to i delete these?

---

### Post by cwsnyder on 2012-11-11
Open a terminal and enter **sudo nautilus** or whatever your preferred file manager, enter your password as required, then click on the trash container in the file manager and tell it to delete the trash.

---

### Post by dan0804smith on 2012-11-11
> **cwsnyder said:**
> Open a terminal and enter **sudo nautilus** or whatever your preferred file manager, enter your password as required, then click on the trash container in the file manager and tell it to delete the trash.


when i try that it says  

Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by cwsnyder on 2012-11-11
Another try, since they didn't like that.  Open a terminal and type the following:```
sudo su
cd /root/.local/share/Trash/files
```Make sure you enter your password correctly.  Also **make very sure** you are in the correct folder.  You might want to type **ls** to check if the files are there you want to erase, then just enter:```
rm -rf *.* 
```Type **ls**again to make sure you deleted the files. Type **exit** to exit root, and type **exit** or press Ctrl-D to close the terminal.

**These are a very, very dangerous set of commands.  Make sure you are _exactly_ where you are supposed to be before you execute them!!!**

---

### Post by dan0804smith on 2012-11-11
> **cwsnyder said:**
> Another try, since they didn't like that.  Open a terminal and type the following:```
sudo su
cd /root/.local/share/Trash/files
```Make sure you enter your password correctly.  Also **make very sure** you are in the correct folder.  You might want to type **ls** to check if the files are there you want to erase, then just enter:```
rm -rf *.* 
```Type **ls**again to make sure you deleted the files. Type **exit** to exit root, and type **exit** or press Ctrl-D to close the terminal.

**These are a very, very dangerous set of commands.  Make sure you are _exactly_ where you are supposed to be before you execute them!!!**

Thank you for your patients with me but i am still having trouble.  This is what happend.

daniel@daniel-HP-Pavilion-dv6-Notebook-PC:~$ sudo su
[sudo] password for daniel: 
root@daniel-HP-Pavilion-dv6-Notebook-PC:/home/daniel# cd /root/.local/share/Trash/files
bash: cd: /root/.local/share/Trash/files: No such file or directory
root@daniel-HP-Pavilion-dv6-Notebook-PC:/home/daniel# cd /root/.local/share/Trash/files
bash: cd: /root/.local/share/Trash/files: No such file or directory

---

### Post by cwsnyder on 2012-11-11
My best thought is that the files you 'found' were a figment of **find**'s cache.  Don't worry about them, trash has already taken care of them.

---

