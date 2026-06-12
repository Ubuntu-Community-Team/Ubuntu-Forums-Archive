---
title: "Help mounting and sharing Apple Time Capsule mount on Ubuntu 22.04"
date: 2023-02-14
forum: General Help
---

### Post by zoe08 on 2023-02-14
[COLOR=#1C1C1C][FONT=&quot]I've not been able to access my Time Capsule drive. [Looks like "NTLMv1" got removed from the kernel]("https://askubuntu.com/questions/1434083/connect-to-apple-time-capsule-on-22-04-ntlm-v1#:%7E:text=UPDATE%20%2D%20I%20found%20an%20active%20discussion%20on%20the%20removal%20of%20NTLMv1%20from%20the%20kernel.%20For%20now%20it%20seems%20the%20only%20option%20is%20to%20downgrade%20the%20kernel"). I could downgrade the kernel, but that's my last option.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]I want to be able to mount the drive on my Ubuntu server to share it with docker containers on the same server, and Windows pc's.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]As of now, my workaround is to mount the drive to the container and share it with my network.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]I'm working on a solution with a docker container. Basically I'm using a ubuntu:xenial image, with macvlan driver. I'm creating a timecapsule user, installing samba (configuring it), [afpfs-ng]("https://github.com/simonvetter/afpfs-ng") and mounting the time capsule drive to a directory, hoping to share the directory with the rest of my network (Windows pcs, linux pc's, more containers). The solution works, I'm able to mount the time capsule drive, but only as a root. When I execute the command to mount the drive as the timecapsule user I get an error. If I do it as root it works. If I try to ls the directory with the timecapsule user I get permission denied. I could execute chmod -R to the mounted drive, but The time capsule drive has almost 2GB of files, and I don't want to mess the permission on the drive.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Does anybody have an idea how can I solve this? Is any other workaround I could try?[/FONT][/COLOR]

---

