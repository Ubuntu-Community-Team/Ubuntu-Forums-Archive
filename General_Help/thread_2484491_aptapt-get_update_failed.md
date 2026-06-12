---
title: "apt/apt-get update failed"
date: 2023-02-28
forum: General Help
---

### Post by linuxbp on 2023-02-28
**H**ello people, when I try to do an "apt update" or an "apt-get update" it gives me the following error:
```

Obj:1 http://ar.archive.ubuntu.com/ubuntu jammy InRelease
Des:2 http://ar.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]     
Obj:3 https://dl.winehq.org/wine-builds/ubuntu kinetic InRelease               
Des:4 http://ar.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB]   
Obj:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Ign:6 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages    
Des:7 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [442 kB]
Obj:8 https://packages.microsoft.com/repos/edge stable InRelease               
Des:9 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [198 kB]
Obj:10 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu jammy InRelease
Ign:11 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata
Ign:12 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata
Ign:13 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
Des:14 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [588 kB]
Ign:15 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata
Ign:16 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata
Ign:17 http://ar.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata
Des:6 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [899 kB]
Ign:18 http://ar.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata
Ign:19 http://ar.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata
Des:11 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]
Err:11 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata
  El archivo tiene un tamaño inesperado (101412 != 101420). ¿La sincronización de la réplica está en progreso? [IP: 200.236.31.4 80]
  Hashes of expected file:
   - Filesize:101420 [weak]
   - SHA256:ae1352efa624ddcd18a0d6b8c0135bfa54e95f7ef545321df8b52c0ede2b6c88
   - SHA1:f36a4ab11c23168a38d9e356c5692cb7fe60038c [weak]
   - MD5Sum:48d1f8d8809d6c3a889583a07c6304e8 [weak]
  Release file created at: Tue, 28 Feb 2023 14:14:19 +0000
Des:12 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [13,5 kB]
Err:12 http://ar.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata
  
Des:13 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [863 kB]
Des:15 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [268 kB]
Err:15 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata
  
Des:16 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [17,3 kB]
Err:16 http://ar.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata
  
Des:17 http://ar.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Err:17 http://ar.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata
  
Des:18 http://ar.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [7.996 B]
Err:18 http://ar.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata
  El archivo tiene un tamaño inesperado (7980 != 7996). ¿La sincronización de la réplica está en progreso? [IP: 200.236.31.4 80]
  Hashes of expected file:
   - Filesize:7996 [weak]
   - SHA256:363d5db87d759a08c2019b3d27351a8b8273840cd63a09da9c0180c1f051eaa4
   - SHA1:d900d839d6b28f9518be223ae9f80a51bfe236d2 [weak]
   - MD5Sum:f59a674f78b7d6f2f2cd90f770b73d0c [weak]
  Release file created at: Tue, 28 Feb 2023 14:14:58 +0000
Des:19 http://ar.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12,5 kB]
Err:19 http://ar.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata
  
Descargados 3.229 kB en 4s (778 kB/s)        
Leyendo lista de paquetes... Hecho
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-updates/main/dep11/Components-amd64.yml.xz  El archivo tiene un tamaño inesperado (101412 != 101420). ¿La sincronización de la réplica está en progreso? [IP: 200.236.31.4 80]
   Hashes of expected file:
    - Filesize:101420 [weak]
    - SHA256:ae1352efa624ddcd18a0d6b8c0135bfa54e95f7ef545321df8b52c0ede2b6c88
    - SHA1:f36a4ab11c23168a38d9e356c5692cb7fe60038c [weak]
    - MD5Sum:48d1f8d8809d6c3a889583a07c6304e8 [weak]
   Release file created at: Tue, 28 Feb 2023 14:14:19 +0000
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-updates/main/cnf/Commands-amd64.xz  
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/dep11/Components-amd64.yml.xz  
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/cnf/Commands-amd64.xz  
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-updates/multiverse/dep11/Components-amd64.yml.xz  
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-backports/main/dep11/Components-amd64.yml.xz  El archivo tiene un tamaño inesperado (7980 != 7996). ¿La sincronización de la réplica está en progreso? [IP: 200.236.31.4 80]
   Hashes of expected file:
    - Filesize:7996 [weak]
    - SHA256:363d5db87d759a08c2019b3d27351a8b8273840cd63a09da9c0180c1f051eaa4
    - SHA1:d900d839d6b28f9518be223ae9f80a51bfe236d2 [weak]
    - MD5Sum:f59a674f78b7d6f2f2cd90f770b73d0c [weak]
   Release file created at: Tue, 28 Feb 2023 14:14:58 +0000
E: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/jammy-backports/universe/dep11/Components-amd64.yml.xz  
E: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.

```
How can i fix this?

---

### Post by SeijiSensei on 2023-02-28
Put a hash mark ("#") in front of the lines that reference "DEP-11 Metadata" to disable that repository and try again. You have a lot more sources than I do; did you add them yourself? My most recent installation of Kubuntu 22.04 only has these in sources.list:

```

deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse

```

You could also try choosing another repository.

---

### Post by deadflowr on 2023-02-28
*Thread moved to **General Help***

---

