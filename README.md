# OBSERVAÇÃO IMPORTANTE
# As imagens deste tutorial foram testadas apenas em TV Boxes com memória eMMC.
# Não sei se funciona em dispositivos com memória NAND.
# Sempre faça backup da ROM original antes de qualquer modificação.

############################################################
# COMO GRAVAR multitool.img NO CARTÃO SD OU PENDRIVE (LINUX)
############################################################

# Este tutorial ensina como gravar o arquivo multitool.img em um
# cartão microSD ou pendrive para usar em TV Boxes compatíveis
# com LibreELEC.

############################################################
# ATENÇÃO
############################################################

# Tenha certeza absoluta do dispositivo que você vai usar.
# O comando "dd" apaga completamente o dispositivo escolhido.
# Se escolher o dispositivo errado, você pode apagar seu HD ou SSD.

############################################################
# PASSO 1 - BAIXAR A IMAGEM DO MULTITOOL
############################################################

# Baixe a imagem:

# https://github.com/glorioso-tv/LibreELEC/releases/download/LibreELEC/multitool.img


############################################################
# PASSO 2 - DESCOBRIR O DISPOSITIVO DO CARTÃO OU PENDRIVE
############################################################

# Conecte o cartão SD ou pendrive no computador e execute:

lsblk

# Você verá algo parecido com isto:

# sda
# sdb
# sdc

# Normalmente o cartão ou pendrive será algo como:

# /dev/sdc

# IMPORTANTE:
# Use apenas o dispositivo principal.
# NÃO use partições como /dev/sdc1

############################################################
# PASSO 3 - GRAVAR A IMAGEM
############################################################

# Execute o comando abaixo:

sudo dd if=multitool.img of=/dev/sdX bs=4M status=progress

# Substitua sdX pelo dispositivo correto.

# Exemplo:

# sudo dd if=multitool.img of=/dev/sdc bs=4M status=progress

# Aguarde o processo terminar.

############################################################
# PASSO 4 - GARANTIR QUE OS DADOS FORAM GRAVADOS
############################################################

sync

# Esse comando garante que todos os dados foram gravados
# no cartão ou pendrive, evitando corrupção.

############################################################
# PASSO 5 - REMOVER O DISPOSITIVO COM SEGURANÇA
############################################################

sudo eject /dev/sdc


############################################################
# USANDO O MULTITOOL NA TV BOX
############################################################

# 1. Insira o cartão SD na TV Box desligada.

# 2. Conecte:
#    - Cabo HDMI
#    - Fonte de energia

# A TV Box deverá iniciar automaticamente no Multitool.


############################################################
# FAZER BACKUP DA MEMÓRIA INTERNA
############################################################

# Antes de instalar qualquer sistema, faça um backup.

# No menu do Multitool selecione:

# Backup NAND Flash

# ou opção semelhante.

# O backup será salvo automaticamente no cartão SD
# na pasta:

# backups/


############################################################
# COPIANDO A IMAGEM DO SISTEMA PARA O CARTÃO
############################################################

# Depois do backup:

# 1. Retire o cartão da TV Box
# 2. Conecte novamente no computador

# Você verá uma partição chamada:

# Multitool

# Copie a imagem do sistema para a pasta:

# images/

# Exemplo de imagem recomendada:

# https://github.com/glorioso-tv/LibreELEC/releases/download/LibreELEC/LibreELEC-RK322X.arm-12.0-nightly-20250218-6a1e364-rk322x.img


############################################################
# INSTALANDO O SISTEMA NA TV BOX
############################################################

# 1. Coloque novamente o cartão na TV Box
# 2. Ligue a TV Box

# No menu do Multitool selecione:

# Write image to NAND

# Escolha a imagem que você colocou na pasta images/

# Aguarde a instalação terminar.

# Depois remova o cartão SD.


############################################################
# PRONTO
############################################################

# Agora sua TV Box estará com o sistema instalado
# e poderá iniciar diretamente da memória interna
# com o novo sistema (como LibreELEC).
