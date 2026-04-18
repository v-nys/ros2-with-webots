Deze patch voegt Webots met ROS-integratie toe aan [een image van PXL](https://github.com/PXLAIRobotics/ROS2_Development_Environment/).

De patch file bevat de wijzigingen in kwestie. Zie Github Actions om te begrijpen hoe hij wordt toegepast.

Om een patch te maken:

- start van de Dockerfile uit de originele repo
- pas eventueel de patch uit deze repo toe om voort te bouwen op wat hier staat
- doe verdere aanpassingen
- check build door script "01_build_image.sh" uit te voeren
- kopieer de Dockerfile, bijvoorbeeld naar AltDockerfile
- `git restore Dockerfile`
- `diff Dockerfile AlterDockerfile > add_webots_bridge.patch` (en verplaats de patch naar deze repository)

Om het eindresultaat te runnen:

- clone de originele repo van PXL ergens
- pas "pxl_ros2_jazzy_vnc_image/02_run_container.sh" aan door `vincentnys/` toe te voegen voor de imagenaam (check Github Actions voor de concrete waarde en vergeet de `/` niet!)
- run dan script het script
  - laat de terminal open staan zo lang je gebruik wil maken van de container
  - dit zou een Docker container moeten starten die luistert op poort 5901
- start een VNC viewer (bijvoorbeeld RealVNC) en verbind op `localhost:5901` (het is niet erg dat deze connectie unencrypted is)
- om Webots te starten open je een terminal en typ je `webots`
- indien je wil dat bepaalde data (bijvoorbeeld een Webots project) langer leeft dan de container, kan je een Docker volume mount toepassen
- na het sluiten van de connectie kan het zijn dat verbinden niet meer werkt en dat je moet herstarten om dt opnieuw te kunnen doen
