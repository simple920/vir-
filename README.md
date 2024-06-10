@echo off
:Start
REM Open Notepad
start "" notepad.exe

REM Give Notepad some time to open
timeout /t 2 > nul

REM Send keystrokes to Notepad
REM Note: You might need to install 'nircmd' or 'sendkeys' tool to send keystrokes in some Windows versions
echo set WshShell = WScript.CreateObject("WScript.Shell") > script.vbs
echo WshShell.AppActivate "Untitled - Notepad" >> script.vbs
echo WshShell.SendKeys "Hello, World!" >> script.vbs
echo WshShell.SendKeys "{ENTER}" >> script.vbs
cscript /nologo script.vbs
del script.vbs

REM Loop to prevent closing
:Loop
timeout /t 1 > nul
goto Loop
