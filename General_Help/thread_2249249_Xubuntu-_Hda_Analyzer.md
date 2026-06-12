---
title: "Xubuntu- Hda Analyzer"
date: 2014-10-20
forum: General Help
---

### Post by clment2 on 2014-10-20
Hello everybody,

I'm xubuntu and i tried to change Mic Jack into a Headphone Jack because i broke the headphone in the other one which leave me impossible to use it.
After running "Sudo python run.py"

I got that:
arnaud@arnaud:~$ sudo python run.py
Using temporary directory: /tmp/hda-analyzer
You may remove this directory when finished or if you like to
download the most recent copy of hda-analyzer tool.
File cached /tmp/hda-analyzer/hda_analyzer.py
File cached /tmp/hda-analyzer/hda_guilib.py
File cached /tmp/hda-analyzer/hda_codec.py
File cached /tmp/hda-analyzer/hda_proc.py
File cached /tmp/hda-analyzer/hda_graph.py
File cached /tmp/hda-analyzer/hda_mixer.py
Downloaded all files, executing hda_analyzer.py
Invalid AFG subtree for codec ATI R6xx HDMI?
Traceback (most recent call last):
  File "/tmp/hda-analyzer/hda_analyzer.py", line 546, in <module>
    sys.exit(main(sys.argv))
  File "/tmp/hda-analyzer/hda_analyzer.py", line 523, in main
    if read_nodes(sys.argv[1:]) == 0:
  File "/tmp/hda-analyzer/hda_analyzer.py", line 89, in read_nodes
    read_nodes2(c.card, i)
  File "/tmp/hda-analyzer/hda_analyzer.py", line 69, in read_nodes2
    c.analyze()
  File "/tmp/hda-analyzer/hda_codec.py", line 1186, in analyze
    VERBS['GET_SUBSYSTEM_ID'], 0)
  File "/tmp/hda-analyzer/hda_codec.py", line 1050, in rw
    verb = (nid << 24) | (verb << 8) | param
TypeError: unsupported operand type(s) for <<: 'NoneType' and 'int'
Exception AttributeError: "'NoneType' object has no attribute 'close'" in <bound method HDACodec.__del__ of <hda_codec.HDACodec instance at 0xb5e2a1cc>> ignored
Exception AttributeError: "'NoneType' object has no attribute 'close'" in <bound method HDACard.__del__ of <hda_codec.HDACard instance at 0xb5dc288c>> ignored
Exception AttributeError: "'NoneType' object has no attribute 'close'" in <bound method AlsaMixer.__del__ of <hda_mixer.AlsaMixer instance at 0xb5dc28ec>> ignored


I tried to google it but i couldn't solve the problem.
Can somebody help me :) Thank you

---

