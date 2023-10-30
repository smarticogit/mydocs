# SPRINT 08

### 16/10/2023 - 27/10/2023

## Portal Service
>
- Listagem de  FORM
  - Método: GET
  - URL:
    - `/form`  
    - `/form?type=`
>
- Criar Collab:
  - Validações:
    - Se TYPE é AttentionTest e se recebe objeto attentionTest
    - Se TYPE é Insight e se recebe formId
    - Se formId existe na base de dados
    - Método: POST
    - URL:  `/collab`
    - Payload:
    ```
        {
            "title": "Teste de Collab 04",
            "type": "INSIGHT",
            "formId": "652803bcf06b1e73c2f99dc2"
        }
        ou
        {
            "title": "Teste de Collab 05",
            "type": "ATTENTIONTEST",
            "attentionTest": {
                "duration": 123, 
                "url": "http://localhost:3000",
                "quiz": [
                    {
                    "quizId": 1, 
                    "order": 1, 
                    "question": "Quantos animais Moisés colocou na Arca?",
                    "options": [
                        {
                            "isCorrect": true, 
                            "option": "Nenhum"
                        },
                        {
                            "isCorrect": false, 
                            "option": "Um de cada espécie"
                        }
                    ]
                    }
                ]
            }
        }

    ```
>
- Editar Collab:
  - Validações:
    - Se collabId existe;
    - Se Type da collab é AttentionTest e recebe formId, lança erro;
    - Se Type da collab é Insight e recebe attentionTest, lança erro;
    - Se TYPE for Insight verifica se formId existe na base;
    - Metódo: PUT
    - URL: `/collab/id`
      - Payload:
      ```
        {
            "title": "Teste de Collab 01 Updated",
            "type": "INSIGHT",
            "formId": "652e99e7071ad83c171bb906"
        }

        ou

        {
            "title": "Teste de Collab Attention 01",
            "type": "ATTENTIONTEST",
            "attentionTest": {
                "duration": 123, 
                "url": "string",
                "quiz": [
                    {
                    "quizId": 1, 
                    "order": 1, 
                    "question": "Quantos anos eu me chamo?",
                    "options": [
                        {
                            "isCorrect": true, 
                            "option": "30"
                        },
                        {
                            "isCorrect": false, 
                            "option": "Valdir"
                        }
                    ]
                }
                ]
                }
        }
      ```
>
- Listagem de Collabs
  - Listagem Paginada de Collabs: SEARCH, SORT, SORTBY, PAGE, LIMIT
    - SORTBY: status, title, createdAt, type
  - Metódo: GET
  - URL: `/collab`
>
- Obter Collab
  - Validações:
  - Verifica se collabId existe na base de dados
  - Método: GET
  - URL:  `/collab/id`
>
- Deletar Collab
  - Validações:
  - Verifica se collabId existe na base de dados
  - Se collab TYPE for diferente de CREATED, lança erro;
  - Método: DELETE
  - URL: `/collab/id`
