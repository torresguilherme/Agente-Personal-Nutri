# 🤖 AI Fitness Coach: Seu Personal Trainer e Nutricionista Virtual com n8n
Este projeto é um sofisticado fluxo de trabalho (workflow) na plataforma n8n que implementa um AI Fitness Coach, um assistente virtual que atua como personal trainer e nutricionista. A solução é projetada para interagir com usuários através de aplicativos de mensagens (como WhatsApp ou Telegram), compreendendo não apenas texto, mas também mensagens de voz e imagens.

✨ Visão Geral do Fluxo
O objetivo é oferecer uma experiência de coaching de saúde e bem-estar altamente personalizada e interativa. O usuário pode enviar suas dúvidas, relatar seu progresso, enviar fotos de suas refeições ou áudios com perguntas, e o assistente de IA responderá de forma coerente e contextual, mantendo um histórico das conversas para oferecer conselhos cada vez mais precisos.

(Nota: Substitua o link acima pelo link da sua imagem no repositório, se desejar)

🏋️‍♂️ Principais Funcionalidades 🥗
Comunicação Multimodal: O assistente é capaz de processar três tipos de entrada:

Texto: Conversa direta por chat.

Áudio: Transcrição automática de mensagens de voz para texto.

Imagem: Análise de imagens para identificar alimentos, equipamentos de ginástica, etc.

Dupla Persona (Personal Trainer e Nutricionista): O agente de IA é instruído (via prompt engineering) a atuar com conhecimento em ambas as áreas, oferecendo desde planos de treino até análises de dietas.

Memória de Longo Prazo: O fluxo salva o histórico de interações em um banco de dados, permitindo que o agente de IA se "lembre" de conversas passadas para fornecer um acompanhamento contínuo e personalizado.

Arquitetura Robusta em Branches: O fluxo processa cada tipo de mídia em um ramo (branch) dedicado antes de unificar a informação para o processamento do agente principal, garantindo eficiência e organização.

Integração Flexível: Utilizando um gatilho de Webhook, o sistema pode ser facilmente conectado a diversas APIs de mensagens.

⚙️ Detalhamento do Fluxo
O workflow opera em uma sequência lógica e poderosa, dividida em etapas claras:

Recepção e Triagem (Webhook + Switch):

Tudo começa com um Webhook que recebe a mensagem do usuário.

Um nó Switch imediatamente analisa o tipo de mensagem recebida e a direciona para um dos três ramos de processamento.

Ramo de Processamento de Áudio (Vermelho):

Se o usuário enviar uma mensagem de voz, este ramo é ativado.

Ele obtém o arquivo de áudio, o converte para um formato compatível (ex: .mp3) e utiliza um serviço de Speech-to-Text (como o Whisper da OpenAI) para transcrever o áudio em texto.

Ramo de Processamento de Imagem (Azul):

Se o usuário enviar uma foto (ex: um prato de comida), este ramo é ativado.

Ele obtém o arquivo de imagem e o envia para um modelo de visão computacional (como o GPT-4o/GPT-4V da OpenAI) que analisa e descreve o conteúdo da imagem em texto. Por exemplo: "A imagem mostra um prato com filé de salmão grelhado, brócolis e uma porção de quinoa."

Ramo de Gerenciamento de Texto (Amarelo):

Se a mensagem for um texto simples, ela passa por uma rotina que gerencia o histórico da conversa, buscando mensagens anteriores para dar contexto ao agente de IA.

Ponto de Convergência e O Cérebro: Agente de IA (Verde):

Todos os ramos convergem para cá, entregando uma entrada de texto padronizada (seja o texto original, a transcrição do áudio ou a descrição da imagem).

O AI Agent é o núcleo do sistema. Ele é composto por:

Modelo de Linguagem (OpenAI Chat Model): O motor que gera as respostas (ex: GPT-4o).

Memória (Super memoria / ReAct Memory): Permite que o agente acesse conversas passadas, garantindo coerência e personalização.

Ferramentas (Tools): O agente pode ser equipado com ferramentas para realizar ações específicas, como buscar informações nutricionais em uma base de dados externa ou calcular calorias.

O agente recebe o texto do usuário e o histórico da conversa, e formula uma resposta inteligente, agindo como o "Fitness Coach".

Saída e Persistência de Dados:

A resposta gerada pelo agente é enviada de volta para o usuário através da plataforma de mensagens.

Simultaneamente, a nova interação (pergunta do usuário e resposta da IA) é salva em um banco de dados para alimentar a memória de longo prazo.

🚀 Exemplos de Uso
Nutrição: O usuário envia uma foto do seu almoço. A IA analisa a imagem, identifica os alimentos, estima as calorias e macronutrientes, e oferece um feedback: "Ótima escolha! Este prato parece bem balanceado. O salmão é rico em ômega-3. Continue assim!"

Treino: O usuário envia um áudio: "Estou na academia, o que posso fazer para o treino de costas hoje?". A IA transcreve o áudio e responde com uma sugestão de treino, como: "Claro! Que tal começar com 3 séries de puxada alta, seguidas de 3 séries de remada curvada?".

Acompanhamento: O usuário envia um texto: "Não estou conseguindo evoluir no supino.". A IA consulta o histórico e responde: "Notei que nas últimas 2 semanas você manteve a mesma carga. Talvez seja hora de tentarmos uma periodização. Que tal incluir uma semana de choque com mais repetições e menos carga?".

🛠️ Tecnologias e Pré-requisitos
Uma instância do n8n (Cloud ou auto-hospedada).

Uma API de Mensagens configurada para enviar webhooks (ex: WhatsApp Business API, Telegram Bot API).

Uma chave de API da OpenAI (para os modelos de linguagem, transcrição e visão).

Um Banco de Dados para armazenamento do histórico (ex: Supabase, PostgreSQL, MySQL).
<img width="1696" height="587" alt="Personal 1" src="https://github.com/user-attachments/assets/f3718122-98b7-4b8f-b75a-9cf031686706" />
<img width="1888" height="839" alt="Personal 2" src="https://github.com/user-attachments/assets/e2d73818-8534-46bc-b22e-4b1f4edbd270" />
<img width="1236" height="848" alt="Personal 3" src="https://github.com/user-attachments/assets/9095b4ab-0146-4a07-beba-cadea43cda17" />
<img width="1267" height="912" alt="Personal 4" src="https://github.com/user-attachments/assets/0eddd18f-83bd-402e-985d-2006ef8aee70" />
<img width="1276" height="912" alt="Personal 5" src="https://github.com/user-attachments/assets/382befe5-b823-469e-b9ac-eb5a4f445353" />








