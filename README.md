# 🔌 Conectando via SSH à Raspberry Pi

1. **Baixe o Tailscale:**  
   Acesse [https://tailscale.com/download](https://tailscale.com/download) e faça o download da aplicação compatível com seu sistema operacional.

2. **Instale e faça login:**  
   Instale o Tailscale e faça login com o e-mail da equipe:  
   `hambis.sustentavel@gmail.com`

3. **Encontre a Raspberry Pi na rede:**  
   Após o login, acesse a seção **"My Devices"** ou **"Network Devices"**.  
   Localize o dispositivo chamado **raspberrypi** e clique nele para copiar o IP gerado pelo Tailscale.

4. **Conecte via SSH:**  
   No terminal, execute o comando abaixo, substituindo `<IP_DA_RASPBERRY>` pelo IP copiado:

   ```bash
   ssh hambis-pi@<IP_DA_RASPBERRY>	
   ```

5. **Autenticação:**  
   Será solicitada a senha do usuário `hambis-pi`. Utilize:  
   Senha: `Hambis321`

6. **Conexão estabelecida:**  
   Agora você está conectado remotamente à Raspberry Pi via SSH.

---

# 🧠 Executando múltiplos códigos com `tmux`

7. **Inicie a sessão `tmux` chamada `server`:**

   ```bash
   tmux new -s server	
   ```
	
   Em seguida, execute os seguintes comandos dentro da sessão:

   ```bash
   conda activate data-env
   cd Documents/raspberry-pi-main/rasp/
   python server.py	
   ```

   Para sair da sessão mantendo o código em execução, pressione:  
   `Ctrl + B`, depois `D`

---

8. **Inicie a sessão `tmux` chamada `ngrok`:**

   ```bash
   tmux new -s ngrok	
   ```
	
   Em seguida, execute o seguinte comando dentro da sessão:

   ```bash
   ngrok http 127.0.0.1:5000	
   ```

   Para sair da sessão mantendo o código em execução, pressione:  
   `Ctrl + B`, depois `D`

---

# ⚙️ Comandos úteis do `tmux`

- **Voltar para a sessão `server`:**

  ```bash
  tmux attach -t server	
  ```

- **Voltar para a sessão `ngrok`:**

  ```bash
  tmux attach -t ngrok	
  ```

- **Encerrar um código rodando dentro de uma sessão:**

  ```bash
  tmux attach -t nome_da_sessao
  ```
  Dentro da sessão, pressione `Ctrl + C` para interromper o script e depois digite:
  ```bash
  exit
  ```

- **Matar uma sessão diretamente (sem reabrir):**

  ```bash
  tmux kill-session -t nome_da_sessao
  ```

- **Listar sessões `tmux` ativas:**

  ```bash
  tmux ls
  ```

---

