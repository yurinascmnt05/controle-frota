# 🚗 Sistema de Controle de Frota PWA

Solução inteligente para gestão de veículos corporativos com agendamento em tempo real, controle de quilometragem e histórico de uso.

## 🛠️ Tecnologias
- **Frontend:** HTML5, CSS3 (Mobile First), JavaScript (ES6+).
- **Backend:** Firebase Firestore (Banco de dados NoSQL em tempo real).
- **Autenticação:** Firebase Auth (E-mail/Senha).
- **PWA:** Service Workers para instalação direta no smartphone.

## 📋 Funcionalidades Principais
- **Agenda Semanal:** Interface estilo Microsoft Teams para reserva de horários.
- **Status Dinâmico:** Cards mudam de cor (Verde/Amarelo/Vermelho) conforme a disponibilidade e horário atual.
- **Trava de Segurança:** Validação por e-mail que impede a retirada de múltiplos veículos ou o uso indevido de reservas alheias.
- **Gestão de KM:** Registro obrigatório de odômetro na devolução com trava de erro humano (não aceita KM menor que o de saída).
- **Locais de Devolução:** Seleção rápida via interface otimizada (GHPC, G-MOTION, KPT).

## 🗄️ Estrutura de Dados (Firestore)
### Coleção: `carros`
- `nome`: String (Identificação do veículo)
- `status`: String (disponivel / em_uso)
- `ultimoKM`: Number (Odômetro atual)
- `agendaGrade`: Map (Mapeamento de slots ex: "SEG-14:00" -> {email, nome})
- `localDevolucao`: String (Último local registrado)

### Coleção: `historico`
- Registra cada movimentação contendo: `usuario`, `carroNome`, `acao`, `kmSaida`, `kmChegada` e `data`.