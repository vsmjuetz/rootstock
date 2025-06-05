# Inhaltsverzeichnis

- [Erstellen eines neuen Manuskripts](#erstellen-ein-neues-Manuskript)

* [Mit Setup-Skript](#using-setup-script)

* [Manuelle Konfiguration](#manuelle-Konfiguration)

* [Repository erstellen](#repository erstellen)

* [Kontinuierliche Integration](#kontinuierliche-Integration)

+ [GitHub-Aktionen](#github-actions)

+ [SSH-Bereitstellungsschlüssel](#ssh-deploy-key)

- [Fügen Sie den öffentlichen Schlüssel zu GitHub hinzu](#add-the-public-key-to-github)

- [Fügen Sie den privaten Schlüssel zu GitHub hinzu](#add-the-private-key-to-github)

+ [Vorschau von Pull-Request-Builds mit AppVeyor](#previewing-pull-request-builds-with-appveyor)

* [README-Updates](#readme-updates)

* [Abschließen](#abschließen)

- [Upstream-Rootstock-Änderungen zusammenführen](#merging-upstream-rootstock-changes)

* [Standardzweig](#default-branch)

_Generiert mit [markdown-toc](https://ecotrust-canada.github.io/markdown-toc/)_

# Erstellen eines neuen Manuskripts

Diese Anweisungen beschreiben, wie Sie ein neues Manuskript basierend auf dem [`manubot/rootstock`](https://github.com/manubot/rootstock/) Repository erstellen.

Der Prozess kann etwas schwierig sein, da er einige Schritte erfordert, die schwer zu automatisieren sind.

Sie müssen diese Schritte jedoch nur einmal für jedes Manuskript ausführen.

Diese Schritte sollten in einer Befehlszeilen-Shell (Terminal) ausgeführt werden, beginnend in dem Verzeichnis, in dem der Manuskriptordner erstellt werden soll.

Setup wird unter Linux, macOS und Windows unterstützt.

Das Windows-Setup erfordert [Git Bash](https://gitforwindows.org/) oder [Windows-Subsystem für Linux](https://docs.microsoft.com/en-us/windows/wsl/faq).

## Setup-Skript verwenden

Das Erstellen eines neuen Manuskripts mit GitHub-Aktionen, dem empfohlenen Standard-CI-Dienst (siehe unten), kann einfach mit dem [Setup-Skript](https://github.com/manubot/rootstock/blob/main/setup.bash) erreicht werden.

Dadurch werden einfach die unten in der manuellen Konfiguration beschriebenen Schritte ausgeführt.

Verwenden Sie den folgenden Befehl, um `setup.bash` zu kopieren und auszuführen.

Sie können den Code überprüfen, der ausgeführt wird [hier](https://github.com/manubot/rootstock/blob/main/setup.bash).

````sh

Bash <( curl --location https://github.com/manubot/rootstock/raw/main/setup.bash )

````

Das Skript führt Sie dann durch den Prozess des Klonens des Rootstock-Repository, nimmt die für die Verwendung von GitHub-Aktionen erforderlichen Änderungen vor, bearbeitet die README, um auf Ihr Repo zu zeigen und die Änderungen zu committen.

Ihr neues Manuskript-Repository ist dann bereit, damit Sie damit beginnen können, Ihre eigenen Inhalte hinzuzufügen.

Dieses Skript erstellt das Remote-Repository nicht für Sie, daher werden Sie aufgefordert, manuell ein leeres GitHub-Repository unter <https://github.com/new> zu erstellen.

Initialisieren Sie das Repository nicht, außer wenn Sie optional eine Beschreibung hinzufügen.

### CLI

Es gibt auch eine Befehlszeilenschnittstelle für Benutzer, die Manuskripte in großem Maßstab und auf automatisierte Weise erstellen möchten.

Weitere Informationen finden Sie in der Hilfe.

````sh

Bash-Setup.bash --Hilfe

````

## Manuelle Konfiguration

Wenn Sie das obige Setup-Skript nicht verwenden möchten, um Ihr neues Manuskript-Repository zu konfigurieren, können Sie die Schritte stattdessen manuell ausführen.

Zuerst müssen Sie zwei Umgebungsvariablen (`OWNER` und `REPO`) konfigurieren.
