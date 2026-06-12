---
title: "Ubuntu Docker on Windows Tutorial (Not working)"
date: 2018-07-01
forum: General Help
---

### Post by humanjhawkins on 2018-07-01
I'm attempting to use the Ubuntu Docker tutorial at: 
   [https://tutorials.ubuntu.com/tutorial/tutorial-windows-ubuntu-hyperv-containers#0](https://tutorials.ubuntu.com/tutorial/tutorial-windows-ubuntu-hyperv-containers#0)

On step 7 at "[COLOR=#333333][FONT=&quot].[/FONT][/COLOR][COLOR=#333333][FONT=&quot]\dockerd[/FONT][/COLOR][COLOR=#333333][FONT=&quot].[/FONT][/COLOR][COLOR=#333333][FONT=&quot]exe [/FONT][/COLOR][COLOR=#333333][FONT=&quot]-[/FONT][/COLOR][COLOR=#333333][FONT=&quot]D [/FONT][/COLOR][COLOR=#333333][FONT=&quot]--[/FONT][/COLOR][COLOR=#333333][FONT=&quot]data[/FONT][/COLOR][COLOR=#333333][FONT=&quot]-[/FONT][/COLOR][COLOR=#333333][FONT=&quot]root C[/FONT][/COLOR][COLOR=#333333][FONT=&quot]:[/FONT][/COLOR][COLOR=#333333][FONT=&quot]\lcow[/FONT][/COLOR]", the process seems (?) to be stalled with the following output:


[INDENT]DEBU[2018-07-01T14:49:01.353115700-07:00] Config reload - waiting signal at Global\docker-daemon-config-9008[/INDENT]
[INDENT]INFO[2018-07-01T14:49:01.354145000-07:00] API listen on //./pipe/docker_engine[/INDENT]

Was unsure if that was as intended (just listening as it should be?), so eventually proceeded with "[COLOR=#333333][FONT=&quot].[/FONT][/COLOR][COLOR=#333333][FONT=&quot]\docker[/FONT][/COLOR][COLOR=#333333][FONT=&quot].[/FONT][/COLOR][COLOR=#333333][FONT=&quot]exe pull ubuntu[/FONT][/COLOR]". This gave a clear failure message as:
[INDENT]Using default tag: latest[/INDENT]
[INDENT]latest: Pulling from library/ubuntu[/INDENT]
[INDENT]no matching manifest for windows/amd64 in the manifest list entries
[/INDENT]

I'm assuming paths changed, etc? (xenial was replaced by bionic in an early step). Can anyone offer suggestions or point me to resources that may help?

Thanks in advance.

---

