# Delphi Build Eventer
*for Delphi 6-7*
Install this package and before build Delphi will try to start BeforeBuild.bat in project folder.
I use this for archive my sources and inject this archive to EXE file as a resource.
For this case you need:
1. Instal BuildEventer package;
2. Create file **BeforeBuild.bat** in your project folder with content:
```cmd
REM -ma5 - RAR5 format
REM -m5 - compression rate
REM -s - solid archive type
REM -dh - open shared files
rar a -ma5 -m5 -s -dh -x*.exe -x*.dcu -x*.~* -x*.ini -x*.rar -x*.zip sources.rar *.*
```
3. Create file **sources.rc** in your project folder with content:
```
sources RCDATA sources.rar
```
4. Insert follow detective to your project code (I add it in DPT file at the beginning):
```
{$R 'sources.res' 'sources.rc'}
```
Compile once or twice.